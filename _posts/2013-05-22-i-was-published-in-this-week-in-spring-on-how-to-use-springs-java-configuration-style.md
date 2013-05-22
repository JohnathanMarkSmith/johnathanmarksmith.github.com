---
layout: post
title: "I was published in 'This Week in Spring' on how to use Spring's Java Configuration Style"
description: "I was published in 'This Week in Spring' on how to use Spring's Java Configuration Style"
categories: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration ]
tags: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration ]
comments: false
---

Yahooooooooo...... I was published in 'This Week in Spring' on how to use Spring's Java Configuration Style.

<div style="text-align: center">
<img src="/images/springsource.jpg" alt="Installing Jboss on Linux with Johnathan Mark Smith" >
</div>

Below is the example that was posted:

Consider replacing Spring XML configuration with JavaConfig

Using Spring XML configuration is so 2000's the time has come to push the XML away and look at JavaConfig.

Here is the main code to my sample project

{% highlight bash %}
public class Main
{

    private static final Logger LOGGER = getLogger(Main.class);

    public static void main(String[] args)
    {
        // in this setup, both the main(String[]) method and the JUnit method both specify that
        ApplicationContext context = new AnnotationConfigApplicationContext( HelloWorldConfiguration.class );
        MessageService mService = context.getBean(MessageService.class);
        HelloWorld helloWorld = context.getBean(HelloWorld.class);

        /**
         * Displaying default messgae
         */
        LOGGER.debug("Message from HelloWorld Bean: " + helloWorld.getMessage());

        /**
         *   Saving Message to database
         */
        Message message = new Message();
        message.setMessage(helloWorld.getMessage());
        mService.SaveMessage(message);

        /**
         * Settting new message in bean
         */
        helloWorld.setMessage("I am in Staten Island, New York");
        LOGGER.debug("Message from HelloWorld Bean: " + helloWorld.getMessage());

        /**
         * Saving Message in database.
         */
        message.setMessage(helloWorld.getMessage());
        mService.SaveMessage(message);

        /**
         * Getting messages from database
         *    - display number of message(s)
         *    - display each message in database
         */
        List<Message> myList = mService.listMessages();
        LOGGER.debug("You Have " + myList.size() + " Message(s) In The Database");

        for (Message i : myList)
        {
            LOGGER.debug("Message: ID: " + i.getId() + ", Message: " + i.getMessage() + ".");
        }
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
@Import(DatabaseConfiguration.class)
@ComponentScan
@PropertySource("classpath:application.properties")
public class HelloWorldConfiguration {

    @Bean
    public HelloWorld getHelloWorld(Environment env) {
        HelloWorld hw = new HelloWorld();
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
