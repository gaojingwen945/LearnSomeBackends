# LearnSomeBackends
后台学习笔记

# 学习路径

## spring framework体系结构（[spring framework体系结构](https://www.cnblogs.com/ywlaker/p/6136625.html)）：core、aop、data access、web、test 

## spring webapp目录结构：[spring web app的结构](https://www.cnblogs.com/hustdc/p/9548150.html) 

​    src

​	— main 

​    	— java    *源代码* 

​    	— resources目录    *存放各种资源文件；Intellij在生成war包的时候将resources目录下的文件都拷贝到了WEB-INF的classes目录下和java包的class文件平行存放。* 

​    	— WEB-INF目录    *该目录下存放classes文件夹、lib文件夹和web.xml；WEB-INF目录是JAVA web应用的安全目录，客户端是不能访问的，只能服务器端访问。*

WEB-INF目录下有两个配置文件需要注意：

1. web.xml，web app入口（[Spring MVC的web.xml配置详解(转)](https://www.cnblogs.com/apimhnkj/p/10404891.html)）：配置文件的根为\<web-app>\</web-app>，tomcat加载war的时候会去读该入库文件，该文件中指定：1、servlet、servlet-mapping拦截规则；2、filter过滤器（编码格式等）；3、context-param contextConfigLocation配置；4、欢迎页、错误页；5、session-config会话配置（如超时时长session-timeout）； 
2. root-context.xml（或param-name-servlet.xml、application.xml）文件，由web.xml中的contextConfigLocation属性指定（[applicationContext.xml文档解析](https://blog.csdn.net/shenhaiyushitiaoyu/article/details/84100822)）：配置文件的根为\<beans>\</beans>，配置组件扫描器、依赖注入、bean属性等。 

## spring boot配置文件pom.xml：配置文件的根为\<project>\</project>，设置编码格式、framework版本、依赖组件、构建配置 

## 如何部署服务

- 部署服务到远端：用的是jenkins
- 尝试部署到本地：

​            部署到“Tomcat Server -> Local”一直不成功，9.0和8.5都是这样，总是报 No Spring WebApplicationInitializer types detected on classpath，用浏览器打开url，报404  --> 是因为这个项目的pom.xml里面只配了jetty插件，没有配tomcat-maven-plugin吗？ --> 可是尝试加上了也还是不行

​            用Jetty插件可以，先用jetty吧，注意jetty端口号配的是9090

- 部署一个前端项目：

​            可以用gulp：

​            1、先去到页面目录：xxx-webapp/src/main/webapp/assets/your_business_dir

​            2、npm i 安装需要的nodes

​            3、npm i gulp -g 安装gulp

​            4、gulp -v 检查gulp安装

​            5、gulp 运行项目

## postman：入门 - done，进阶 - todo 

## 抓包：Charles 

## 看一下springmvc的框架中，如何讲解controller，service，DAO 这几层 

## aop框架or微服务：微服务这一块，就涉及到调度，不过这些都是现成的，然后再去如何提升性能，如何容灾。 

## 如果用微服务，肯定是无状态的，不用过多考虑session，但是nginx做基本的负载，几种负载的方式原理和配置需要熟悉 

## 其次redis做数据层的缓存，查询多变化少的，需要做缓存。然后在哪个层面做缓存都需要考虑。 

## 其次是数据库压力还是过大的时候，分表分库，分布式事务等 

## 另外需要了解一下如消息队列，这些来控制前端的请求量 

## 怎么估算资源需求量？客户端数、请求量、对应到的线程数、服务器数？ 