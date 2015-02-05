---
layout: post
title: "How to create a runnable JAR file with Gradle"
description: "How to create a runnable JAR file with Gradle"
categories: [ Java, Gradle ]
tags: [ Java, Gradle ]
comments: false
---

This post will show you how we can compile and package a simple Java Project using Gradle into a runnable JAR file

### Project Layout  

The default project layout of a Java project with Gradle is following (just like Maven): 
{% highlight bash %}
- The src/main/java directory contains the source code.
- The src/main/resources directory contains the resources (such as properties files).
- The src/test/java directory contains the test classes.
- The src/test/resources directory contains the test resources.  
{% endhighlight %}

So now make a new folder where you would like the project to start:
{% highlight bash %}
mkdir runnablejar
cd runnablejar  
{% endhighlight %}
 Let’s create the project layout by using the following commands:
{% highlight bash %}
mkdir -p src/main/java
mkdir -p src/main/resources
mkdir -p src/test/java
mkdir -p src/test/resources  
{% endhighlight %}

As you can see from above the project layout looks just like a Maven project. 

### Creating the Main Class  

Let’s create the main class for this project and make it display "Hello World" 
cd into src/main/java and create the package layout. 

{% highlight bash %}
mkdir -p com/johnathanmarksmith/gradle  
{% endhighlight %}


We have the project layout created and also the package layout so now it’s time to create the Main Class 

{% highlight bash %}
vi com/johnathanmarksmith/gradle/HelloWorld.java  
{% endhighlight %}

 and insert the following lines:
 
 {% highlight bash %}
package com.johnathanmarksmith.gradle;
public class HelloWorld
{
    spublic static void main(String[] args) 
    { 
        System.out.println("Hello World!"); 
    } 
}   
{% endhighlight %}

### Creating the Gradle Build File..  

The next step is to create the Gralde Build file, Go back to the root of the project.   cd ../../.. And create the build file 

{% highlight bash %}
vi build.gradle   
{% endhighlight %}

Now add the following lines:

{% highlight bash %}
 apply plugin: 'java' 
 
 jar { 
        baseName = 'smith' 
        version = '1.0' 
        manifest { 
                     attributes 'Main-Class': 'com.johnathanmarksmith.gradle.HelloWorld' } 
     }    
{% endhighlight %}

Building the project and creating the JAR 
To build the project and to create the JAR you need to run the following command gradle build Executeing the JAR 

{% highlight bash %}
java -jar ./build/libs/smith-1.0.jar   
{% endhighlight %}


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
