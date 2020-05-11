spring最简单的一个例子
https://blog.csdn.net/qq_36838191/article/details/81264276

spring入门篇
https://segmentfault.com/a/1190000013700859

两个特点：
1.控制翻转 IOC
2.依赖注入 DI

Spring容器可以归为两种类型
Bean工厂，BeanFactory【功能简单】
应用上下文，ApplicationContext【功能强大，一般我们使用这个】
每个ApplicationContext创建自己的对象

对象建立的写法
1.构造函数
<bean id="user" class="User">
    <!--通过constructor这个节点来指定构造函数的参数类型、名称、第几个-->
    <constructor-arg index="0" name="id" type="java.lang.String" value="1"></constructor-arg>
    <constructor-arg index="1" name="username" type="java.lang.String" value="zhongfucheng"></constructor-arg>
</bean>

2.property
<bean id="person" class="Person">
    <property name="name" value="winter"></property>
    <property name="hello" ref="helloWorld"></property>
</bean>

3.工厂静态方法
<bean id="user" class="Factory" factory-method="getBean" >
</bean>

4.工厂非静态方法（需要先建立工厂对象）
<!--首先创建工厂对象-->
<bean id="factory" class="Factory"/>
<!--指定工厂对象和工厂方法-->
<bean id="user" class="User" factory-bean="factory" factory-method="getBean"/>

5.通过注解方式建立对象
通过注解来配置信息就是为了简化IOC容器的配置，注解可以把对象添加到IOC容器中、处理对象依赖关系
使用注解步骤：
1）先引入context名称空间
xmlns:context="http://www.springframework.org/schema/context"
2）开启注解扫描器
<context:component-scan base-package=""></context:component-scan>

@ComponentScan扫描器
@Configuration表明该类是配置类
@Component 指定把一个对象加入IOC容器--->@Name也可以实现相同的效果【一般少用】
@Repository 作用同@Component； 在持久层使用
@Service 作用同@Component； 在业务逻辑层使用
@Controller 作用同@Component； 在控制层使用
@Resource 依赖关系
如果@Resource不指定值，那么就根据类型来找，相同的类型在IOC容器中不能有两个
如果@Resource指定了值，那么就根据名字来找

6.通过java方式
编写一个java类，使用@Configuration修饰该类
被@Configuration修饰的类就是配置类

用配置类创建bean:
1.使用@Bean来修饰方法，该方法返回一个对象。
2.不管方法体内的对象是怎么创建的，Spring可以获取得到对象就行了。
3.Spring内部会将该对象加入到Spring容器中
4.容器中bean的ID默认为方法名

对象创建时可以设置单例模式或者多例模式
单例模式：
当我们使用singleton【单例】的时候，从IOC容器获取的对象都是同一个
当使用singleton的时候，对象在IOC容器之前就已经创建了（lazy-init仅对单例模式有用，使得对象在使用的时候才创建）
多例模式：
当我们使用prototype【多例】的时候，从IOC容器获取的对象都是不同的
当使用prototype的时候，对象在使用的时候才创建

init-method和destroy-method
如果我们想要对象在创建后，执行某个方法，我们指定为init-method属性就行了。
如果我们想要IOC容器销毁后，执行某个方法，我们指定destroy-method属性就行了。
  <bean id="user" class="User" scope="singleton" lazy-init="true" init-method="" destroy-method=""/>

  Bean创建细节总结
  /**
   * 1) 对象创建： 单例/多例
   *     scope="singleton", 默认值， 即 默认是单例    【service/dao/工具类】
   *  scope="prototype", 多例；                 【Action对象】
   *
   * 2) 什么时候创建?
   *       scope="prototype"  在用到对象的时候，才创建对象。
   *    scope="singleton"  在启动(容器初始化之前)， 就已经创建了bean，且整个应用只有一个。
   * 3)是否延迟创建
   *       lazy-init="false"  默认为false,  不延迟创建，即在启动时候就创建对象
   *       lazy-init="true"   延迟初始化， 在用到对象的时候才创建对象
   *    （只对单例有效）
   * 4) 创建对象之后，初始化/销毁
   *       init-method="init_user"       【对应对象的init_user方法，在对象创建之后执行 】
   *    destroy-method="destroy_user"  【在调用容器对象的destroy方法时候执行，(容器用实现类)】
   */

       
