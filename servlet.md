Servlet生命周期可分为5个步骤
1.加载Servlet。当Tomcat第一次访问Servlet的时候，Tomcat会负责创建Servlet的实例
2.初始化。当Servlet被实例化后，Tomcat会调用init()方法初始化这个对象
3.处理服务。当浏览器访问Servlet的时候，Servlet 会调用service()方法处理请求
4.销毁。当Tomcat关闭时或者检测到Servlet要从Tomcat删除的时候会自动调用destroy()方法，让该实例释放掉所占的资源。
一个Servlet如果长时间不被使用的话，也会被Tomcat自动销毁
5.卸载。当Servlet调用完destroy()方法后，等待垃圾回收。如果有需要再次使用这个Servlet，会重新调用init()方法进行初始化操作。

提交表单的两种方式
https://blog.csdn.net/zeephom/article/details/79609999
https://blog.csdn.net/beishafengjiang/article/details/73527121?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2
