mvn archetype:generate -DgroupId=tutorials.spring-boot.jersey -DartifactId=tutorials.spring-boot.jersey.actuator -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false

Steps
-----
- Create application.properties
- Add dependency "spring-boot-starter-web" to enable Spring MVC
- Add dependency "spring-boot-starter-actuator" to enable Spring Actuator
- Change the mapping path of Spring MVC dispatcher servlet in "application.properties"

If above steps work, when starting the application we will see two servlet beans registered (Jersey & Spring MVC)
    2017-10-26 17:25:02.924  INFO 3405 --- [ost-startStop-1] o.s.b.w.servlet.ServletRegistrationBean  : Mapping servlet: 'com.configuration.JerseyConfig' to [/rest/*]
    2017-10-26 17:25:02.925  INFO 3405 --- [ost-startStop-1] o.s.b.w.servlet.ServletRegistrationBean  : Mapping servlet: 'dispatcherServlet' to [/system/*]


$ curl -i -k -H "Content-Type: application/json" -d '{"text":"Hello world"}' -X POST http://localhost:8080/rest/messages
$ curl -i -k -H "Content-Type: application/json" -d '{"text":"Hello message 2"}' -X POST http://localhost:8080/rest/messages
$ curl -i -k -H "Accept: application/json" http://localhost:8080/rest/messages

$ curl -i -k -H "Accept: application/json" http://localhost:8080/system/health
$ curl -i -k -H "Accept: application/json" http://localhost:8080/system/trace


References
----------
https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#production-ready
https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-endpoints.html
https://docs.spring.io/spring-boot/docs/current/reference/html/howto-actuator.html
