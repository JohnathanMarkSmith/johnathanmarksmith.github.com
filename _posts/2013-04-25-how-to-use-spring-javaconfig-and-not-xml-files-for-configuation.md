---
layout: post
title: "How to use Spring JavaConfig and not XML files for configuation"
description: "How to use Spring JavaConfig and not XML files for configuation"
categories: [ Spring, Java, JavaConfig, Programming ]
tags: [ Spring, Java, JavaConfig, Programming ]
comments: false
---

Consider replacing Spring XML configuration with JavaConfig

Using Spring XML configuration is so 2000's the time has come to push the XML away and look at JavaConfig.

Here is the main code to my sample project

{% highlight bash %}
public class MainApp
{
    public static void main(String[] args)
    {
        ApplicationContext context = new AnnotationConfigApplicationContext(HelloWorldConfig.class);
        HelloWorld helloWorld = context.getBean(HelloWorld.class);


        System.out.println(helloWorld.getMessage());

        helloWorld.setMessage("I am in Staten Island, New York");
        System.out.println(helloWorld.getMessage());
    }
}
{% endhighlight %}

You can see from this code that the ApplicationContext is mapped to a HelloWorldConfig.class file its not using a XML file.  Below is the code to the HelloWorldConfig.class.

{% highlight bash %}
/**
 * Date:   4/25/13 / 9:37 AM
 * Author: Johnathan Mark Smith
 * Email:  john@johnathanmarksmith.com
 * <p/>
 * Comments:
 *    This is the config example of how to use JavaConfig and not XML Files:
 *
 *    This Would be the same as the following
 *    <beans>
 *       <bean id="helloWorld" class="com.johnathanmarksmith.HelloSpringJavaBasedJavaConfig.bean.HelloWorld" />
 *    </beans>
 *
 */

@Configuration
@ComponentScan(basePackages = {"com.johnathanmarksmith.HelloSpringJavaBasedJavaConfig.bean"})
@PropertySource("classpath:application.properties")
public class HelloWorldConfig
{

    @Autowired
    Environment env;

    @Bean
    public HelloWorld getHelloWorld()
    {
        HelloWorld hw = new HelloWorld();

       /*
        This is use to read in the property from the application.properties file
       */

        hw.setMessage(env.getProperty("bean.text"));

        return hw;
    }
}
{% endhighlight %}

You can see how easy it is to use JavaConfig and Not XML.. 

You can download the source code to this at my github project. 
<a href="https://github.com/JohnathanMarkSmith/HelloSpringJavaBasedJavaConfig">https://github.com/JohnathanMarkSmith/HelloSpringJavaBasedJavaConfig</a>

Now that's it. have fun with Spring JavaConfig. 

### Down and Run Project

If you would like to download the project from GitHub and run it just follow the following commands:

{% highlight bash %}
git clone git@github.com:JohnathanMarkSmith/HelloSpringJavaBasedJavaConfig.git
cd HelloSpringJavaBasedJavaConfig
mvn packge
cd target
java -jar HelloSpringJavaBasedJavaConfig.jar
{% endhighlight %}

LIFE IS SO EASY WORKING WITH GIT, MAVEN, SPRING....



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

 

{% include JB/setup %}
