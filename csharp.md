#### MVC路由
----------
1. 默认路由设置  
    App_Start -> RouteConfig.cs 中有下面的定义  
    ```
    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Department", action = "Index", id = UrlParameter.Optional }
    );
    ```
2. WebApi中的路由  
    WebApi默认路由是通过http的方法（get/set/put/delete）来匹配对应的action，不需要指定action名字  
    ```
    config.Routes.MapHttpRoute(
        name: "DefaultApi",
        routeTemplate: "api/{controller}/{id}",
        defaults: new { id = RouteParameter.Optional }
    );
    ```
    路由配置会找到controller之后会根据请求类型来自动匹配action。  
    可以在其中配置正则表达式来约束规范匹配内容。  
    
3. WebApi中的自定义路由  
    ```
     config.Routes.MapHttpRoute(
        name: "ActionApi",
        routeTemplate: "actionapi/{controller}/{action}/{id}",
        defaults: new { id = RouteParameter.Optional }
     );
    ```
    公司使用的路由配置方法，简单直观，直接配置到controller/action。但是似乎不推荐。

    ```
    config.Routes.MapHttpRoute(
        name: "TestApi",
        routeTemplate: "testapi/{controller}/{ordertype}/{id}",
        defaults: new { ordertype="aa", id = RouteParameter.Optional }
    );
    ```  
    在这种配置过程中，如果有多个方法是同一个参数，同一种传递类型，那么可以通过[Route("Order/Save1")]
    

4. 配置实现过程  
    - WebApi服务启动之后，会执行全局配置文件Global.asax.cs的 `protected void Application_Start(){GlobalConfiguration.Configure(WebApiConfig.Register);}` 方法，通过参数委托执行WebApiConfig.cs里面的 `public static void Register(HttpConfiguration config)` 这个方法，将所有配置的路由信息添加到 HttpRouteCollection 对象中（MVC里面可能是RoutCollection对象）保存起来。这里的HttpRoutCollection对象的实例名是Routes，这个很重要，后面要用到。

    - 当我们发送请求到WebApi服务器的时候，比如我们访问http://localhost:21528/api/Order这个url的时候，请求首先还是会被UrlRoutingModule监听组件截获，然后，将截获的请求在Routes路由集合中匹配到对应的路由模板（如果匹配不到对应的路由模板，则返回404），得到对应的IHttpRoute对象。IHttpRoute对象是Routes集合里面匹配到的一个实体。

    - 将IHttpRoute对象交给当前的请求的上下文对象RequestContext处理，根据IHttpRoute对象里面的url匹配到对应的controller，然后再根据http请求的类型和参数找到对应的action。这样一个请求就能找到对应的方法了。 

    [页面原地址](http://www.cnblogs.com/landeanfen/p/5501490.htmllink)