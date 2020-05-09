Tomcat安装较为简单，需要注意要选中jre

Tomcat是一个容器

关于在intellij上配置tomcat
https://www.cnblogs.com/javabg/p/7976977.html

Tomcat分为war部署和war_exploded这两种，区别如下
https://blog.csdn.net/linjpg/article/details/73322881

常见的错误是运行时接口被占用

webinf目录下的资源是不能直接被浏览器访问的

https://segmentfault.com/a/1190000013124026
一般在webinf下建立classes目录和lib目录

浏览器输入urt时：
1.发现tomcat中的web.xml中配置有这个映射路径
2.查看映射路径名
3.通过映射路径名找到配置servlet的名字
4.通过servlet的名字找到servlet编译后class文件存放的位置
5.执行servlet
