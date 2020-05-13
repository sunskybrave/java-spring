http://c.biancheng.net/view/4392.html

Spring MVC 的工作流程如下：
1.客户端请求提交到 DispatcherServlet。
2.由 DispatcherServlet 控制器寻找一个或多个 HandlerMapping，找到处理请求的 Controller。
3.DispatcherServlet 将请求提交到 Controller。
4.Controller 调用业务逻辑处理后返回 ModelAndView。
5.DispatcherServlet 寻找一个或多个 ViewResolver 视图解析器，找到 ModelAndView 指定的视图。
6.视图负责将结果显示到客户端。
