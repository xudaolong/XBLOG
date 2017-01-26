> Jersey

```

使用URI
支持MIME类型的响应数据，包括JSON/XML/JPEG等
使用HTTP GET/POST/DELETE/PUT（对应查找、新增、删除、修改）
###JSR 311(JAX-RS)和Jersey Jersey是JSR 311的Java实现，可以快速的实现RESTful Web Service。Jersey的最新版本为2.6。其主要包含三个部分：

核心服务器（Core Server）：通过提供JSR 311 中标准化的注释和API 标准化，您可以用直观的方式开发RESTful Web 服务
核心客户端（Core Client）：Jersey 客户端API 帮助您与REST 服务轻松通信。
集成（Integration）：Jersey 还提供可以轻松集成Spring、Guice、Apache Abdera 的库。

```

> 依赖包

```

commons-beanutils.jar
commons-lang.jar
commons-logging.jar
ezmorph-1.0.2.jar
javax.servlet.api.jar
javax.ws.rs-api : 处理媒体类型等
json-lib.jar

```

> 常用注解

```

@Path 定义资源的相对URI
@GET 意味着以下方法可以响应HTTP GET方法
@Produces 响应的MIME类型

@Path("/users/{username}")
这个例子中，{username}即为用户输入的数据，例如用户输入Weiwei，则URL定位到 http://example.com/users/Weiwei
对应的组件:
    public String getUser(@PathParam("username") String userName) {
        ...
    }
一个@Path的内容是否以"/"开头都没有区别，同样是否以"/"结尾也没有什么区别
@Path 位于方法上便是 子资源 分两种方式:


@Produces("text/plain")
指定了资源所产生和发送给 客户端的MIME类型，这里指定了类型为纯文本类型。
@Produces 会覆盖类层面的@Produces
@Produces({"application/xml", "application/json"})
public String doGetAsXmlOrJson() {
    ...
}

@Consumes({"application/xml", "application/json"})
指定所消费的类型的格式，这里指定为XML和JSON，即可以 接收 这种类型格式的文件作为输入。

所有媒体类型(*/*)byte[]
java.lang.String
java.io.Reader (inbound only)
java.io.File
javax.activation.DataSource
javax.ws.rs.core.StreamingOutput (outbound only)

XML 媒体类型 (text/xml, application/xml and application/...+xml)
javax.xml.transform.Source
javax.xml.bind.JAXBElement
应用了 JAXB 类的应用 (使用了 @XmlRootElement 或者 @XmlType 的类型)

Form 表单内容(application/x-www-form-urlencoded)
MultivaluedMap

纯文本 (text/plain)java.lang.Boolean
java.lang.Character
java.lang.Number

@FormParam稍有特殊，因为它提取信息，先是请求所表示的MIME媒体类型为 application/x-www-form-urlencoded
，并且符合指定的 HTML 编码的形式，正如这里所描述的。此参数提取对于 HTML 表单请求是非常有用的
@FormParam 注释是特别的，仅可利用资源和子资源的方法。这是因为它从请求实体中提取信息

@MatrixParam 从 URL 路径提取信息. 

@HeaderParam 从 HTTP 头部提取信息。 

@CookieParam从关联在 HTTP 头部的 cookies 里提取信息。

@BeanParam 用法  , 相当于把参数放进去 

public class MyBeanParam {
    @PathParam("p")
    private String pathParam;

    @MatrixParam("m")
    @Encoded
    @DefaultValue("default")
    private String matrixParam;

    @HeaderParam("header")
    private String headerParam;

    private String queryParam;

    public MyBeanParam(@QueryParam("q") String queryParam) {
    this.queryParam = queryParam;
    }

    public String getPathParam() {
    return pathParam;
    }
    ...
}


@POST
public void post(@BeanParam MyBeanParam beanParam, String entity) {
    final String pathParam = beanParam.getPathParam(); // contains injected path parameter "p"
    ...
}



@Singleton 
资源将是单例模式，不受请求范围管理,子资源定位方法返回一个类，这意味着运行时将托管资源的实例及其生命周期。相反，如果方法返回的是实例，那么注释将没有效果，返回的实例将被使用。

@Path("/item")
public class ItemResource {
    @Path("content")
    public Class<ItemContentSingletonResource> getItemContentResource() {
        return ItemContentSingletonResource.class;
    }
}

@Singleton
public class ItemContentSingletonResource {
    // this class is managed in the singleton life cycle
}


```

> 注入规则

```

@Path("{id:\\d+}")
public class InjectedResource {
    // 注入到属性
    @DefaultValue("q") @QueryParam("p")
    private String p;

    // 注入到构造函数参数
    public InjectedResource(@PathParam("id") int id) { ... }

    // 注入到资源参数
    @GET
    public String get(@Context UriInfo ui) { ... }

    // 注入子资源方法参数
    @Path("sub-id")
    @GET
    public String get(@PathParam("sub-id") String id) { ... }

    // 注入子资源方法参数定位器方法参数
    @Path("sub-id")
    public SubResource getSubResource(@PathParam("sub-id") String id) { ... }

    // 注入 bean setter 方法
    @HeaderParam("X-header")
    public void setHeader(String header) { ... }
}


@Path("resource")
public static class SummaryOfInjectionsResource {
    @QueryParam("query")
    String param; // injection into a class field 注入类的属性


    @GET
    public String get(@QueryParam("query") String methodQueryParam) {
        // injection into a resource method parameter 注入资源的方法参数
        return "query param: " + param;
    }

    @Path("sub-resource-locator")
    public Class<SubResource> subResourceLocator(@QueryParam("query") String subResourceQueryParam) {
        // injection into a sub resource locator parameter注入子资源定位器参数
        return SubResource.class;
    }

    public SummaryOfInjectionsResource(@QueryParam("query") String constructorQueryParam) {
        // injection into a constructor parameter注入构造器的参数
    }


    @Context
    public void setRequest(Request request) {
        // injection into a setter method注入setter方法
        System.out.println(request != null);
    }
}

public static class SubResource {
    @GET
    public String get() {
        return "sub resource";
    }
}

```

# 应用的部署和运行时的环境

> ResourceConfig 简化组件的注册,如扫描根资源、类提供者提供的路径或一组包名的集合。所有 JAX-RS 组件类都会手动注册或者扫描期间找到的类都会自动添加到 getClasses 所返回的类的集合中,另外部署时可参考[Servlet容器模型（二）部署描述文件](http://blog.csdn.net/cl05300629/article/details/9339205)

```

public class MyApplication extends ResourceConfig {
    public MyApplication() {
        register(org.glassfish.jersey.server.filter.UriConnegFilter.class);
        register(org.glassfish.jersey.server.validation.ValidationFeature.class);
        register(org.glassfish.jersey.server.spring.SpringComponentProvider.class);
        register(org.glassfish.jersey.grizzly2.httpserver.GrizzlyHttpContainerProvider.class);
        property(ServerProperties.METAINF_SERVICES_LOOKUP_DISABLE, true);
    }
}

    <servlet>
        <servlet-name>Jersey Web Application</servlet-name>
        <servlet-class>org.glassfish.jersey.servlet.ServletContainer</servlet-class>
        <init-param>
            <param-name>javax.ws.rs.Application</param-name>
            <param-value>com.gzmpc.pc.MainApp</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>


<Servlet>元素

1、<servlet-name>元素：必须选，定义servlet名称，在DD文件中应该唯一，可通过servletConfig的getServletName()方法检索；

2、<servlet-class>元素：制定servlet完整名称，需带包

WEB-INF目录中的classes目录和lib目录中JAR文件会被自动添加到容器的类路径中，不需设置类路径

3、<init-param>元素：向servlet传递初始化参数，每个<int-param>有仅有一组<param-name>和<param-value>子元素，可通过ServletConfig接口的getInitParameter()方法检索初始化参数；

4、<load-on-startup>元素：一般的servlet是在被请求时由容器装入内存，这只一个正数则在启动时载入该servlet，值小的优先装入，负数或者没有指定，容器将根据需要决定何时装入servlet



```


> [使用 Spring Data JPA 简化 JPA 开发](http://www.cnblogs.com/eggbucket/archive/2012/10/16/2726302.html)


> [MIME类型大全](http://www.cnblogs.com/zhongcj/archive/2008/11/03/1325293.html)
