---
layout: post
title: "How To Use Spring RESTTeample To Post Data to a Web Service with Authentication"
description: "How To Use Spring RESTTeample To Post Data to a Web Service with Authentication"
categories: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration, Spring MVC, Web, REST, RESTTemplate ]
tags: [ Spring, Java, JavaConfig, Programming, Spring Java Configuration, Spring MVC, Web, REST, RESTTemplate ]
comments: false
---

###  Using Spring RESTTemplate to Post Objects to RESTful web services that has Authentication with Spring's Java Configuration (JavaConfig) style with Maven, JUnit, Log4J


In this example I am going to show you how to post data to a RESTful web service in Java using Spring, Spring Java Configuration and more


### Web Service Code

Let's take a quick look at the Spring MVC Web Service code on the server:

    @Controller
    @RequestMapping("/api")
    class JSonController
    {

        private static final Logger logger = LoggerFactory.getLogger(JSonController.class);



        @RequestMapping(value = "/{id}", method = RequestMethod.POST)
        @ResponseBody
        public User updateCustomer(@PathVariable("id") String id, @RequestBody User user) {

            logger.debug("I am in the controller and got ID: " + id.toString());
            logger.debug("I am in the controller and got user name: " + user.toString());

            return new User("NEW123", "NEW SMITH");
        }


As you can see from the code above the web service is goign to what for a ID and user object to be passed in and then its going to create a new User Object and send it back to the client.

### Time For The Client Code

You can see from the client code below is that we are using Spring RESTTemaple and going to post an User Object to a web server and get one back.


   @PropertySource("classpath:application.properties")
   public class Main
   {

       /**
        * Setting up logger
        */
       private static final Logger LOGGER = getLogger(Main.class);


       public static void main(String[] args) throws IOException
       {
           LOGGER.debug("Starting REST Client!!!!");

           /**
            *
            * This is going to setup the REST server configuration in the applicationContext
            * you can see that I am using the new Spring's Java Configuration style and not some OLD XML file
            *
            */
           ApplicationContext context = new AnnotationConfigApplicationContext(RESTConfiguration.class);

           /**
            *
            * We now get a RESTServer bean from the ApplicationContext which has all the data we need to
            * log into the REST service with.
            *
            */
           RESTServer mRESTServer = context.getBean(RESTServer.class);

           /**
            *
            * Setting up BASIC Authentication access
            *
            */

            HttpClient client = new HttpClient();
           UsernamePasswordCredentials credentials =
                   new UsernamePasswordCredentials(mRESTServer.getUser(), mRESTServer.getPassword());

           client.getState().setCredentials(
                   new AuthScope(mRESTServer.getHost(), 8080, AuthScope.ANY_REALM),
                   credentials);

           CommonsClientHttpRequestFactory commons = new CommonsClientHttpRequestFactory(client);



           /**
            *
            * Setting up data to be sent to REST service
            *
            */
           Map<String, String> vars = new HashMap<String, String>();
           vars.put("id", "INID");

           /**
            *
            * Doing the REST call and then displaying the data/user object
            *
            */
           try
           {

               /*

                   This is code to post and return a user object

                */

               RestTemplate rt = new RestTemplate(commons); // Added the CommonsClientHttpRequestFactory

               rt.getMessageConverters().add(new MappingJacksonHttpMessageConverter());
               rt.getMessageConverters().add(new StringHttpMessageConverter());

               String uri = new String("http://" + mRESTServer.getHost() + ":8080/springmvc-resttemplate-auth-test/api/{id}");

               User u = new User();
               u.setName("Johnathan M Smith");
               u.setUser("JMS");


               User returns = rt.postForObject(uri, u, User.class, vars);

               LOGGER.debug("User:  " + u.toString());

           }
           catch (HttpClientErrorException e)
           {
               /**
                *
                * If we get a HTTP Exception display the error message
                */

               LOGGER.error("error:  " + e.getResponseBodyAsString());

               ObjectMapper mapper = new ObjectMapper();
               ErrorHolder eh = mapper.readValue(e.getResponseBodyAsString(), ErrorHolder.class);

               LOGGER.error("error:  " + eh.getErrorMessage());

           }
           catch(Exception e)
           {
               LOGGER.error("error:  " + e.getMessage());

           }
       }

   }


You can see from the above code how easy it is to use RESTTeample to post data to a web service.



You can see how easy it is to use Spring's Java Configuration (JavaConfig) style and Not XML.. The time of using XML files with Springs is over...

### Download The Source

You can checkout the project from github.

    git clone git@github.com:JohnathanMarkSmith/springmvc-resttemplate-auth-test.git
    cd springmvc-resttemplate-auth-test.git


If you have any questions or comments please email me at john@johnathanmarksmith.com or checkout my web site http://JohnathanMarkSmith.com



{% include JB/setup %}
