---
layout: post
title: "How To Setup BASIC Authentication with Spring Web Services"
description: "How To Setup BASIC Authentication with Spring Web Services"
categories: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration, Spring MVC, Web, REST, RESTTemplate ]
tags: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration, Spring MVC, Web, REST, RESTTemplate ]
comments: false
---


This is a very basic example of using Spring MVC, REST, Spring  and Spring Security, Spring Test Framework using Spring's Java configuration.

The first part of this is to create a configuration class for the web app.  below is a sample of the configuration class we are going to use:

    @Configuration
    @EnableWebMvc
    @ComponentScan(basePackages = {"com.johnathanmsmith.mvc.web"})
    @ImportResource("/WEB-INF/spring/applicationContext.xml")
    public class WebMVCConfig extends WebMvcConfigurerAdapter
    {

        private static final Logger logger = LoggerFactory.getLogger(WebMVCConfig.class);

        @Bean
        public ViewResolver resolver()
        {
            UrlBasedViewResolver url = new UrlBasedViewResolver();
            url.setPrefix("/views/");
            url.setViewClass(JstlView.class);
            url.setSuffix(".jsp");
            return url;
        }

        @Override
        public void addResourceHandlers(ResourceHandlerRegistry registry)
        {
            logger.debug("setting up resource handlers");
            registry.addResourceHandler("/resources/").addResourceLocations("/resources/**");
        }

        @Override
        public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer)
        {
            logger.debug("configureDefaultServletHandling");
            configurer.enable();
        }

        @Bean
        public SimpleMappingExceptionResolver simpleMappingExceptionResolver()
        {
            SimpleMappingExceptionResolver b = new SimpleMappingExceptionResolver();

            Properties mappings = new Properties();
            mappings.put("org.springframework.web.servlet.PageNotFound", "p404");
            mappings.put("org.springframework.dao.DataAccessException", "dataAccessFailure");
            mappings.put("org.springframework.transaction.TransactionException", "dataAccessFailure");
            b.setExceptionMappings(mappings);
            return b;
        }
    }


Next you have to setup the web.xml file to use the above configuration class, we do this but setting the contectConfigLocation to the package of the configuration class.

We also setup the Spring Security Filter Chain pointing to the  applicationContext.xml file that points to my-security.xml.

See below for the web.xml code:

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xmlns="http://java.sun.com/xml/ns/javaee"
             xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
             version="2.5">
        <servlet>
            <servlet-name>Spring MVC Dispatcher Servlet</servlet-name>
            <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
            <init-param>
                <param-name>contextClass</param-name>
                <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
            </init-param>
            <init-param>
                <param-name>contextConfigLocation</param-name>
                <param-value>com.johnathanmsmith.mvc.web.config</param-value>
            </init-param>
            <load-on-startup>1</load-on-startup>
        </servlet>

        <servlet-mapping>
            <servlet-name>Spring MVC Dispatcher Servlet</servlet-name>
            <url-pattern>/</url-pattern>
        </servlet-mapping>

        <filter>
            <filter-name>springSecurityFilterChain</filter-name>
            <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
        </filter>
        <filter-mapping>
            <filter-name>springSecurityFilterChain</filter-name>
            <url-pattern>/*</url-pattern>
        </filter-mapping>

        <context-param>
            <description>The Spring configuration files.</description>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/spring/applicationContext.xml</param-value>
        </context-param>

        <listener>
            <description>The Spring context listener.</description>
            <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
        </listener>

    </web-app>


Now you can see that we setup BASIC authentication in the my-security.xml file using Spring secuirty

    <?xml version="1.0" encoding="UTF-8"?>
    <beans:beans xmlns="http://www.springframework.org/schema/security"
                 xmlns:beans="http://www.springframework.org/schema/beans"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                 xsi:schemaLocation="http://www.springframework.org/schema/beans
                            http://www.springframework.org/schema/beans/spring-beans-3.1.xsd
                            http://www.springframework.org/schema/security
                            http://www.springframework.org/schema/security/spring-security-3.1.xsd">


        <global-method-security pre-post-annotations="enabled"/>

        <http use-expressions="true">
            <intercept-url access="hasRole('ROLE_VERIFIED')" pattern="/json/*"/>
            <intercept-url pattern='/*' access='permitAll'/>

            <logout logout-success-url="/"/>

            <session-management session-fixation-protection="newSession">
                <concurrency-control max-sessions="1"/>
            </session-management>

            <http-basic />
        </http>


        <authentication-manager>
            <authentication-provider>
                <user-service>
                    <user name="test" password="test" authorities="ROLE_VERIFIED"/>
                </user-service>

            </authentication-provider>
        </authentication-manager>
    </beans:beans>

Now lets setup a basic JSON controller to sent json data back to the client:

    @Controller
    @RequestMapping("/json")
    class JSonController
    {

        private static final Logger logger = LoggerFactory.getLogger(JSonController.class);

        private MappingJacksonJsonView  jsonView = new MappingJacksonJsonView();


        @RequestMapping(value = "/{name}", method = RequestMethod.GET)
        @ResponseBody
        public User getName(@PathVariable String name, ModelMap model) throws ResourceNotFoundException
        {

            logger.debug("I am in the controller and got user name: " + name);

            /*

                Simulate a successful lookup for 2 users, this is where your real lookup code would go

             */

            if ("JohnathanMarkSmith".equals(name))
            {
                return new User("Johnathan Mark Smith", name);
            }

            if ("Regan".equals(name))
            {
                return new User("Regan Smith", name);
            }

            throw new ResourceNotFoundException("User Is Not Found");
        }

        @RequestMapping(value = "/", method = RequestMethod.GET)
        public ResponseEntity<User> getDisplayDefault(ModelMap model)
        {
            return new ResponseEntity<User>(new User("Johnathan Mark Smith", "JohnathanMarkSmith"), HttpStatus.OK);
        }


        @ExceptionHandler
        public ResponseEntity<ErrorHolder> handle(ResourceNotFoundException e) {
            logger.warn("The resource was not found", e);
            return new ResponseEntity<ErrorHolder>(new ErrorHolder("Uh oh"), HttpStatus.NOT_FOUND);
        }


        class ErrorHolder {
            public String errorMessage;
            @JsonCreator
            public ErrorHolder(@JsonProperty("errorMessage") String errorMessage)
            {
                this.errorMessage = errorMessage;
            }

        }
    }


Thats all it takes..

## Getting The Project and Running It

To get this project and run it you will need to follow the following steps:

    git clone  git@github.com:JohnathanMarkSmith/springmvc-rest-secured-test.git
    cd springmvc-rest-secured-test/
    mvn tomcat7:run

Now open your web brower and goto http://127.0.0.1:8080/springmvc-rest-secured-test/

This its... Have run with it...


If you have any questions or comments please email me at john@johnathanmarksmith.com or checkout my web site http://JohnathanMarkSmith.com

{% include JB/setup %}
