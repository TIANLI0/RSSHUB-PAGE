
---
title: 'SpringBoot+Mybatis配置多数据源及事务方案'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://picsum.photos/400/300?random=8309'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://picsum.photos/400/300?random=8309'
---

<div>   
<h2>前言</h2>
<p>可能由于业务上的某些需求，我们的系统中有时往往要连接多个数据库，这就产生了多数据源问题。</p>
<p>多数据源的情况下，一般我们要做到可以自动切换，此时会涉及到事务注解 Transactional 不生效问题和分布式事务问题。</p>
<p>关于多数据源方案，笔者在网上看过一些例子，然而大部分都是错误示例，根本跑不通，或者没办法兼容事务。</p>
<p>今天，我们就一点点来分析这些问题产生的根源和相应的解决方法。</p>
<h2>一、多数据源</h2>
<p>为了剧情的顺利开展，我们模拟的业务是创建订单和扣减库存。</p>
<p>所以，我们先创建订单表和库存表。注意，把他们分别放到两个数据库中。</p>
<pre><code>CREATE TABLE `t_storage` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `commodity_code` varchar(255) DEFAULT NULL,
  `count` int(11) DEFAULT '0',
  PRIMARY KEY (`id`),
  UNIQUE KEY `commodity_code` (`commodity_code`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

CREATE TABLE `t_order` (
  `id` bigint(16) NOT NULL,
  `commodity_code` varchar(255) DEFAULT NULL,
  `count` int(11) DEFAULT '0',
  `amount` double(14,2) DEFAULT '0.00',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
</code></pre>
<h4>1、数据库连接</h4>
<p>通过YML文件先把两个数据库都配置一下。</p>
<pre><code>spring:
  datasource:
    ds1:
      jdbc_url: jdbc:mysql://127.0.0.1:3306/db1
      username: root
      password: root
    ds2:
      jdbc_url: jdbc:mysql://127.0.0.1:3306/db2
      username: root
      password: root
</code></pre>
<h4>2、配置DataSource</h4>
<p>我们知道，Mybatis执行一条SQL语句的时候，需要先获取一个Connection。这时候，就交由Spring管理器到DataSource中获取连接。</p>
<p>Spring中有个具有路由功能的DataSource，它可以通过查找键调用不同的数据源，这就是<code>AbstractRoutingDataSource</code>。</p>
<pre><code>public abstract class AbstractRoutingDataSource&#123;
    //数据源的集合
    @Nullable
    private Map<Object, Object> targetDataSources;
    //默认的数据源
    @Nullable
    private Object defaultTargetDataSource;
    
    //返回当前的路由键，根据该值返回不同的数据源
    @Nullable
    protected abstract Object determineCurrentLookupKey();
    
    //确定一个数据源
    protected DataSource determineTargetDataSource() &#123;
        //抽象方法 返回一个路由键
        Object lookupKey = determineCurrentLookupKey();
        DataSource dataSource = this.targetDataSources.get(lookupKey);
        return dataSource;
    &#125;
&#125;
</code></pre>
<p>可以看到，该抽象类的核心就是先设置多个数据源到Map集合中，然后根据Key可以获取不同的数据源。</p>
<p>那么，我们就可以重写这个determineCurrentLookupKey方法，它返回的是一个数据源的名称。</p>
<pre><code>public class DynamicDataSource extends AbstractRoutingDataSource &#123;
    @Override
    protected Object determineCurrentLookupKey() &#123;
        DataSourceType.DataBaseType dataBaseType = DataSourceType.getDataBaseType();
        return dataBaseType;
    &#125;
&#125;
</code></pre>
<p>然后还需要一个工具类，来保存当前线程的数据源类型。</p>
<pre><code>public class DataSourceType &#123;

    public enum DataBaseType &#123;
        ds1, ds2
    &#125;
    // 使用ThreadLocal保证线程安全
    private static final ThreadLocal<DataBaseType> TYPE = new ThreadLocal<DataBaseType>();
    // 往当前线程里设置数据源类型
    public static void setDataBaseType(DataBaseType dataBaseType) &#123;
        if (dataBaseType == null) &#123;
            throw new NullPointerException();
        &#125;
        TYPE.set(dataBaseType);
    &#125;
    // 获取数据源类型
    public static DataBaseType getDataBaseType() &#123;
        DataBaseType dataBaseType = TYPE.get() == null ? DataBaseType.ds1 : TYPE.get();
        return dataBaseType;
    &#125;
&#125;
</code></pre>
<p>这些都搞定之后，我们还需要把这个DataSource配置到Spring容器中去。下面这个配置类的作用如下：</p>
<ul>
<li>创建多个数据源DataSource，ds1 和 ds2；</li>
<li>将ds1 和 ds2 数据源放入动态数据源DynamicDataSource；</li>
<li>将DynamicDataSource注入到SqlSessionFactory。</li>
</ul>
<pre><code>@Configuration
public class DataSourceConfig &#123;

    /**
     * 创建多个数据源 ds1 和 ds2
     * 此处的Primary，是设置一个Bean的优先级
     * @return
     */
    @Primary
    @Bean(name = "ds1")
    @ConfigurationProperties(prefix = "spring.datasource.ds1")
    public DataSource getDateSource1() &#123;
        return DataSourceBuilder.create().build();
    &#125;
    @Bean(name = "ds2")
    @ConfigurationProperties(prefix = "spring.datasource.ds2")
    public DataSource getDateSource2() &#123;
        return DataSourceBuilder.create().build();
    &#125;


    /**
     * 将多个数据源注入到DynamicDataSource
     * @param dataSource1
     * @param dataSource2
     * @return
     */
    @Bean(name = "dynamicDataSource")
    public DynamicDataSource DataSource(@Qualifier("ds1") DataSource dataSource1,
                                        @Qualifier("ds2") DataSource dataSource2) &#123;
        Map<Object, Object> targetDataSource = new HashMap<>();
        targetDataSource.put(DataSourceType.DataBaseType.ds1, dataSource1);
        targetDataSource.put(DataSourceType.DataBaseType.ds2, dataSource2);
        DynamicDataSource dataSource = new DynamicDataSource();
        dataSource.setTargetDataSources(targetDataSource);
        dataSource.setDefaultTargetDataSource(dataSource1);
        return dataSource;
    &#125;
    
    
    /**
     * 将动态数据源注入到SqlSessionFactory
     * @param dynamicDataSource
     * @return
     * @throws Exception
     */
    @Bean(name = "SqlSessionFactory")
    public SqlSessionFactory getSqlSessionFactory(@Qualifier("dynamicDataSource") DataSource dynamicDataSource)
            throws Exception &#123;
        SqlSessionFactoryBean bean = new SqlSessionFactoryBean();
        bean.setDataSource(dynamicDataSource);
        bean.setMapperLocations(
                new PathMatchingResourcePatternResolver().getResources("classpath*:mapping/*.xml"));
        bean.setTypeAliasesPackage("cn.youyouxunyin.multipledb2.entity");
        return bean.getObject();
    &#125;
&#125;
</code></pre>
<h4>3、设置路由键</h4>
<p>上面的配置都完成之后，我们还需要想办法动态的改变数据源的键值，这个就跟系统的业务相关了。</p>
<p>比如在这里，我们有两个Mapper接口，创建订单和扣减库存。</p>
<pre><code>public interface OrderMapper &#123;
    void createOrder(Order order);
&#125;
public interface StorageMapper &#123;
    void decreaseStorage(Order order);
&#125;
</code></pre>
<p>那么，我们就可以搞一个切面，在执行订单的操作时，切到数据源ds1，执行库存操作时，切到数据源ds2。</p>
<pre><code>@Component
@Aspect
public class DataSourceAop &#123;
    @Before("execution(* cn.youyouxunyin.multipledb2.mapper.OrderMapper.*(..))")
    public void setDataSource1() &#123;
        DataSourceType.setDataBaseType(DataSourceType.DataBaseType.ds1);
    &#125;
    @Before("execution(* cn.youyouxunyin.multipledb2.mapper.StorageMapper.*(..))")
    public void setDataSource2() &#123;
        DataSourceType.setDataBaseType(DataSourceType.DataBaseType.ds2);
    &#125;
&#125;
</code></pre>
<h4>4、测试</h4>
<p>现在就可以写一个Service方法，通过REST接口测试一下啦。</p>
<pre><code>public class OrderServiceImpl implements OrderService &#123;
    @Override
    public void createOrder(Order order) &#123;
        storageMapper.decreaseStorage(order);
        logger.info("库存已扣减，商品代码:&#123;&#125;，购买数量:&#123;&#125;。创建订单中...",order.getCommodityCode(),order.getCount());
        orderMapper.createOrder(order);
    &#125;
&#125;
</code></pre>
<p>不出意外的话，业务执行完成后，两个数据库的表都已经有了变化。</p>
<p>但此时，我们会想到，这两个操作是需要保证原子性的。所以，我们需要依赖事务，在Service方法上标注Transactional。</p>
<p>如果我们在createOrder方法上添加了Transactional注解，然后在运行代码，就会抛出异常。</p>
<pre><code>### Cause: java.sql.SQLSyntaxErrorException: Table 'db2.t_order' doesn't exist
; bad SQL grammar []; nested exception is java.sql.SQLSyntaxErrorException: 
    Table 'db2.t_order' doesn't exist] with root cause
</code></pre>
<p><strong>这就说明，如果加上了 Spring 的事务，我们的数据源切换不过去了。这又是咋回事呢？</strong></p>
<h2>二、事务模式，为啥不能切换数据源</h2>
<p>要想搞清楚原因，我们就得来分析分析如果加上了Spring事务，它又干了哪些事情呢 ？</p>
<p>我们知道，Spring的自动事务是基于AOP实现的。在调用包含事务的方法时，会进入一个拦截器。</p>
<pre><code>public class TransactionInterceptor&#123;
    public Object invoke(MethodInvocation invocation) throws Throwable &#123;
        //获取目标类
        Class<?> targetClass = AopUtils.getTargetClass(invocation.getThis());
        //事务调用
        return invokeWithinTransaction(invocation.getMethod(), targetClass, invocation::proceed);
    &#125;
&#125;
</code></pre>
<h4>1、创建事务</h4>
<p>在这里面呢，首先就是开始创建一个事务。</p>
<pre><code>protected Object doGetTransaction() &#123;
    //DataSource的事务对象
    DataSourceTransactionObject txObject = new DataSourceTransactionObject();
    //设置事务自动保存
    txObject.setSavepointAllowed(isNestedTransactionAllowed());
    //给事务对象设置ConnectionHolder
    ConnectionHolder conHolder = TransactionSynchronizationManager.getResource(obtainDataSource());
    txObject.setConnectionHolder(conHolder, false);
    return txObject;
&#125;
</code></pre>
<p>在这一步，重点是给事务对象设置了ConnectionHolder属性，不过此时还是为空。</p>
<h4>2、开启事务</h4>
<p>接下来，就是开启一个事务，这里主要是通过ThreadLocal将资源和当前的事务对象绑定，然后设置一些事务状态。</p>
<pre><code>protected void doBegin(Object txObject, TransactionDefinition definition) &#123;
    
    Connection con = null;
    //从数据源中获取一个连接
    Connection newCon = obtainDataSource().getConnection();
    //重新设置事务对象中的connectionHolder，此时已经引用了一个连接
    txObject.setConnectionHolder(new ConnectionHolder(newCon), true);
    //将这个connectionHolder标记为与事务同步
    txObject.getConnectionHolder().setSynchronizedWithTransaction(true);
    con = txObject.getConnectionHolder().getConnection();
    con.setAutoCommit(false);
    //激活事务活动状态
    txObject.getConnectionHolder().setTransactionActive(true);
    //将connection holder绑定到当前线程，通过threadlocal
    if (txObject.isNewConnectionHolder()) &#123;
        TransactionSynchronizationManager.bindResource(obtainDataSource(), txObject.getConnectionHolder());
    &#125;
    //事务管理器，激活事务同步状态
    TransactionSynchronizationManager.initSynchronization();
&#125;
</code></pre>
<h4>3、执行Mapper接口</h4>
<p>开启事务之后，就开始执行目标类真实方法。在这里，就会开始进入Mybatis的代理对象。。哈哈，框架嘛，就各种代理。</p>
<p>我们知道，Mybatis在执行SQL的之前，需要先获取到SqlSession对象。</p>
<pre><code>public static SqlSession getSqlSession(SqlSessionFactory sessionFactory, ExecutorType executorType,
                PersistenceExceptionTranslator exceptionTranslator) &#123;

    //从ThreadLocal中获取SqlSessionHolder，第一次获取不到为空
    SqlSessionHolder holder = TransactionSynchronizationManager.getResource(sessionFactory);
    
    //如果SqlSessionHolder为空，那也肯定获取不到SqlSession;
    //如果SqlSessionHolder不为空，直接通过它来拿到SqlSession
    SqlSession session = sessionHolder(executorType, holder);
    if (session != null) &#123;
        return session;
    &#125;
    //创建一个新的SqlSession
    session = sessionFactory.openSession(executorType);
    //如果当前线程的事务处于激活状态，就将SqlSessionHolder绑定到ThreadLocal
    registerSessionHolder(sessionFactory, executorType, exceptionTranslator, session);
    return session;
&#125;
</code></pre>
<p>拿到SqlSession之后，就开始调用Mybatis的执行器，准备执行SQL语句。在执行SQL之前呢，当然需要先拿到Connection连接。</p>
<pre><code>public Connection getConnection() throws SQLException &#123;
    //通过数据源获取连接
    //比如我们配置了多数据源，此时还会正常切换
    if (this.connection == null) &#123;
        openConnection();
    &#125;
    return this.connection;
&#125;
</code></pre>
<p>我们看openConnection方法，它的作用就是从数据源中获取一个Connection连接。如果我们配置了多数据源，此时是可以正常切换的。如果加了事务，之所以没有切换数据源，是因为第二次调用时，<code>this.connection != null</code>，返回的还是上一次的连接。</p>
<p>这是因为，在第二次获取SqlSession的时候，当前线程是从ThreadLocal中拿到的，所以不会重复获取Connection连接。</p>
<p>至此，在多数据源情况下，如果加了Spring事务，不能动态切换数据源的原因，我们应该都明白了。</p>
<p>在这里，笔者插播一道面试题：</p>
<ul>
<li>Spring是如何保证事务的？</li>
</ul>
<p>那就是将多个业务操作，放到同一个数据库连接中，一起提交或回滚。</p>
<ul>
<li>怎么做到，都在一个连接中呢？</li>
</ul>
<p>这里就是各种ThreadlLocal的运用，想办法将数据库资源和当前事务绑定到一起。</p>
<h2>三、事务模式，怎么支持切换数据源</h2>
<p>上面我们已经把原因搞清楚了，接下来就看怎么支持它动态切换数据源。</p>
<p>其他配置都不变的情况下，我们需要创建两个不同的sqlSessionFactory。</p>
<pre><code>@Bean(name = "sqlSessionFactory1")
public SqlSessionFactory sqlSessionFactory1(@Qualifier("ds1") DataSource dataSource)&#123;
    return createSqlSessionFactory(dataSource);
&#125;

@Bean(name = "sqlSessionFactory2")
public SqlSessionFactory sqlSessionFactory2(@Qualifier("ds2") DataSource dataSource)&#123;
    return createSqlSessionFactory(dataSource);
&#125;
</code></pre>
<p>然后自定义一个CustomSqlSessionTemplate，来代替Mybatis中原有的sqlSessionTemplate，把上面定义的两个SqlSessionFactory注入进去。</p>
<pre><code>@Bean(name = "sqlSessionTemplate")
public CustomSqlSessionTemplate sqlSessionTemplate()&#123;
    Map<Object,SqlSessionFactory> sqlSessionFactoryMap = new HashMap<>();
    sqlSessionFactoryMap.put("ds1",factory1);
    sqlSessionFactoryMap.put("ds2",factory2);
    CustomSqlSessionTemplate customSqlSessionTemplate = new CustomSqlSessionTemplate(factory1);
    customSqlSessionTemplate.setTargetSqlSessionFactorys(sqlSessionFactoryMap);
    customSqlSessionTemplate.setDefaultTargetSqlSessionFactory(factory1);
    return customSqlSessionTemplate;
&#125;
</code></pre>
<p>在定义的CustomSqlSessionTemplate中，其他都一样，主要看获取SqlSessionFactory的方法。</p>
<pre><code>public class CustomSqlSessionTemplate extends SqlSessionTemplate &#123;
    @Override
    public SqlSessionFactory getSqlSessionFactory() &#123;
        //当前数据源的名称
        String currentDsName = DataSourceType.getDataBaseType().name();
        SqlSessionFactory targetSqlSessionFactory = targetSqlSessionFactorys.get(currentDsName);
        if (targetSqlSessionFactory != null) &#123;
            return targetSqlSessionFactory;
        &#125; else if (defaultTargetSqlSessionFactory != null) &#123;
            return defaultTargetSqlSessionFactory;
        &#125;
        return this.sqlSessionFactory;
    &#125;
&#125;
</code></pre>
<p>在这里，重点就是我们可以根据不同的数据源获取不同的SqlSessionFactory。如果SqlSessionFactory不一样，那么在获取SqlSession的时候，就不会在ThreadLocal中拿到，从而每次都是新的SqlSession对象。</p>
<p>既然SqlSession也不一样，那么在获取Connection连接的时候，每次都会去动态数据源中去获取。</p>
<p>原理就是这么个原理，我们来走一把。</p>
<p>修改完配置之后，我们把Service方法加上事务的注解，此时数据也是可以正常更新的。</p>
<pre><code>@Transactional
@Override
public void createOrder(Order order) &#123;
    storageMapper.decreaseStorage(order);
    orderMapper.createOrder(order);
&#125;
</code></pre>
<p>可以切换数据源只是第一步，我们需要的保证可以保证事务操作。假如在上面的代码中，库存扣减完成，但是创建订单失败，库存是不会回滚的。因为它们分别属于不同的数据源，根本不是同一个连接。</p>
<h2>四、XA协议分布式事务</h2>
<p>要解决上面那个问题，我们只能考虑XA协议。</p>
<p>关于XA协议是啥，笔者不再过多的描述。我们只需知道，MySQL InnoDB存储引擎是支持XA事务的。</p>
<p>那么XA协议的实现，在Java中叫做Java Transaction Manager，简称JTA。</p>
<p>如何实现JTA呢？我们借助Atomikos框架，先引入它的依赖。</p>
<pre><code><dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jta-atomikos</artifactId>
    <version>2.2.7.RELEASE</version>
</dependency>
</code></pre>
<p>然后，只需把DataSource对象改成AtomikosDataSourceBean。</p>
<pre><code>public DataSource getDataSource(Environment env, String prefix, String dataSourceName)&#123;
    Properties prop = build(env,prefix);
    AtomikosDataSourceBean ds = new AtomikosDataSourceBean();
    ds.setXaDataSourceClassName(MysqlXADataSource.class.getName());
    ds.setUniqueResourceName(dataSourceName);
    ds.setXaProperties(prop);
    return ds;
&#125;
</code></pre>
<p>这样配完之后，获取Connection连接的时候，拿到的其实是MysqlXAConnection对象。在提交或者回滚的时候，走的就是MySQL的XA协议了。</p>
<pre><code>public void commit(Xid xid, boolean onePhase) throws XAException &#123;
    //封装 XA COMMIT 请求
    StringBuilder commandBuf = new StringBuilder(300);
    commandBuf.append("XA COMMIT ");
    appendXid(commandBuf, xid);
    try &#123;
        //交给MySQL执行XA事务操作
        dispatchCommand(commandBuf.toString());
    &#125; finally &#123;
        this.underlyingConnection.setInGlobalTx(false);
    &#125;
&#125;
</code></pre>
<p>通过引入Atomikos和修改DataSource，在多数据源情况下，即便业务操作中间发生错误，多个数据库也是可以正常回滚的。</p>
<p><strong>另外一个问题，是否应该使用XA协议？</strong></p>
<p>XA协议看起来看起来比较简单，但它也有一些缺点。比如：</p>
<ul>
<li>性能问题，所有参与者在事务提交阶段处于同步阻塞状态，占用系统资源，容易导致性能瓶颈，无法满足高并发场景；</li>
<li>如果协调者存在单点故障问题，如果协调者出现故障，参与者将一直处于锁定状态；</li>
<li>主从复制可能产生事务状态不一致。</li>
</ul>
<p>在MySQL官方文档中也列举了一些XA协议的限制项：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fdev.mysql.com%2Fdoc%2Frefman%2F8.0%2Fen%2Fxa-restrictions.html" target="_blank"> https://dev.mysql.com/doc/refman/8.0/en/xa-restrictions.html</a></p>
<p>另外，笔者在实际的项目里，其实也没有用过，通过这样的方式来解决分布式事务问题，此例仅做可行性方案探讨。</p>
<h2>总结</h2>
<p>本文通过引入SpringBoot+Mybatis的多数据源场景，分析了如下问题：</p>
<ul>
<li>多数据源的配置和实现；</li>
<li>Spring事务模式，多数据源不生效的原因和解决方法；</li>
<li>多数据源，基于XA协议的分布式事务实现。</li>
</ul>
<p>由于篇幅有限，本文示例不包含所有的代码。如有需要，请到GitHub自取。</p>
<p><code>https://github.com/taoxun/multipledb2.git</code></p>
<p><strong>原创不易，客官们点个赞再走嘛，这将是笔者持续写作的动力~</strong></p>
  
</div>
            