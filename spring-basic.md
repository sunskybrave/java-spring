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

最新的可以通过注解方式建立对象
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
