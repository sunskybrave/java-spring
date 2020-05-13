cglib代理

由于静态代理需要实现目标对象的相同接口，那么可能会导致代理类会非常非常多....不好维护---->因此出现了动态代理
动态代理也有个约束：目标对象一定是要有接口的，没有接口就不能实现动态代理.....----->因此出现了cglib代理
cglib代理也叫子类代理，从内存中构建出一个子类来扩展目标对象的功能！

Aop： aspect object programming 面向切面编程
功能： 让关注点代码与业务代码分离！
面向切面编程就是指： 对很多功能都有的重复的代码抽取，再在运行的时候往业务方法上动态植入“切面类代码”。
关注点：

遇到的一个问题
//import org.junit.After;
//import org.junit.Before;
import org.aspectj.lang.annotation.Before;
import org.aspectj.lang.annotation.After;
项目开始缺少jar包，自动补全出错

@Before增强
前置增强
@AfterReturning增强
后置增强
@After增强
相当于Final增强，不管是抛出异常还是正常退出，该增强都会执行
@Around增强
环绕增强
@AfterThrowing增强
抛出增强
@DeclareParents
引介增强
