---
layout: page
title: "Java Interview Questions"
description: "Java Interview Questions"
---

## Java Interview Questions

After over 25 years I still don't like going on interview and getting asked questions that a good programmer/developer dont have to know off the top of his/her head. I good programmer/developer should NOT know all the anwsers but should know how to find them and where to search.  

I am posting this page so programmers/developers can bookmark it and use it.  I am going to be posting some questions that I think everyone will ask.  If you have any questions that I am missing please email me.

# The Java Questions

## Can you have an inner class inside a method and what variables can you access?

Yes, you can have a inner class inside a method and final variables can be accessed.


## What is the difference between String and String Buffer?

1) String objects are constants and immutable whereas StringBuffer objects are not.

2) String class supports constant strings whereas StringBuffer class supports growable and modifiable strings.


## What is interface and its use?

Interface is similar to a class which may contain method’s signature only but not bodies and it is a formal set of method and constant declarations that must be defined by the class that implements it.

Interfaces are useful for:

    a)Declaring methods that one or more classes are expected to implement

    b)Capturing similarities between unrelated classes without forcing a class relationship.

    c)Determining an object’s programming interface without revealing the actual body of the class.


## Difference Between Interface and Abstract Class?

Main difference is methods of a Java interface are implicitly abstract and cannot have implementations. A Java abstract class can have instance methods that implements a default behavior.

Variables declared in a Java interface is by default final. An  abstract class may contain non-final variables.

Members of a Java interface are public by default. A Java abstract class can have the usual flavors of class members like private, protected, etc..

Java interface should be implemented using keyword “implements”; A Java abstract class should be extended using keyword “extends”.

An interface can extend another Java interface only, an abstract class can extend another Java class and implement multiple Java interfaces.

A Java class can implement multiple interfaces but it can extend only one abstract class.

Interface is absolutely abstract and cannot be instantiated; A Java abstract class also cannot be instantiated, but can be invoked if a main() exists.


## What is difference between overloading and overriding?


   a) In overloading, there is a relationship between methods available in the same class whereas in overriding, there is relationship between a superclass method and subclass method. 
   
   b) Overloading does not block inheritance from the superclass whereas overriding blocks inheritance from the superclass. 
   
   c) In overloading, separate methods share the same name whereas in overriding, subclass method replaces the superclass. 

   d) Overloading must have different method signatures whereas overriding must have same signature.



## In Java, what’s the difference between method overloading and method overriding?

 The difference between overriding and overloading in Java is a common source of confusion – but it is fairly simple to understand. Let’s start the discussion by talking more about method overloading. Overloading in Java can occur when two or more methods in the same class share the same name or even if a child class shares a method with the same name as one of it’s parent classes. But, in order to actually have overloaded methods, the methods not only have to have the same name, but there are other conditions that must be satisfied – read below to see what those conditions are.

Suppose we have a class called TestClass which has 2 methods, and both methods have the same name – let’s say that name is “someMethod” – this would be considered to be method overloading if at least one of these 2 things is true:

    1.) The number of parameters is different for the methods   
    2.) The parameter types are different.  

How to NOT overload methods:

It’s important to understand that method overloading is NOT something you can accomplish by doing these 2 things:

    1.) Changing the return type of the method   
    2.) Changing the name of the method parameters, but not changing the parameter types.

Confused? Well, here are some very helpful examples of where overloading would be both valid and invalid:
Examples of Method Overloading in Java – both valid and invalid:

{% highlight bash %}
//compiler error - can't overload based on the   
//type returned -
//(one method returns int, the other returns a float):    

int changeDate(int Year) ;  
float changeDate (int Year);    

//compiler error - can't overload by changing just 
//the name of the parameter (from Month to Year):    

int changeDate(int Month) ;  
float changeDate(int Year);    

//valid case of overloading, since there is an   
//extra parameter in the first method:        

int changeDate(int Year, int Month) ;  
int changeDate(int Year);    

//also a valid case of overloading, since the   
//parameters are of different types:    

int changeDate(float Year) ;  
int changeDate(int Year);  
{% endhighlight %}

Overriding methods is completely different from overloading methods. If a derived class requires a different definition for an inherited method, then that method can be redefined in the derived class. This would be considered overriding. An overridden method would have the exact same method name, return type, number of parameters, and types of parameters as the method in the parent class, and the only difference would be the definition of the method.

Let’s summarize the differences between overloading and overriding. When overloading, one must change either the type or the number of parameters for a method that belongs to the same class. But, overriding a method means that a method inherited from a base class is what’s being changed. 


## What is the role of the clone() method in Java?

protected Object clone() throws CloneNotSupportedException - this method is used to create a copy of an object of a class which implements Cloneable interface. By default it does field-by-field copy as the Object class doesn't have any idea in advance about the members of the particular class whose objects call this method. So, if the class has only primitive data type members then a completely new copy of the object will be created and the reference to the new object copy will be returned. But, if the class contains members of any class type then only the object references to those members are copied and hence the member references in both the original object as well as the cloned object refer to the same object.


## What are Encapsulation, Inheritance and Polymorphism?

Encapsulation is the mechanism that binds together code and data it manipulates and keeps both safe from outside interference and misuse. Inheritance is the process by which one object acquires the properties of another object. Polymorphism is the feature that allows one interface to be used for general class actions.


## What is the difference between this() and super()?

this() can be used to invoke a constructor or method of the same class whereas super() can be used to invoke a super class constructor or method.


## Can a final class have a abstract method?

No. I final class can not have a abstract method in it because when you declare a method in a class as abstract, then the class must be declared as abstract.

"Final" and "Abstract" cannot used at the same time. Any class can be either final or abstract not both!

   Final class means cannot be subclassed.
   Abstract class means must be subclassed.


## Java Interview Question: What is the difference between Array and Vector?

Array is a set of related data type and static whereas vector is a growable array of objects and dynamic.


## Java Interview Question: What is final, finalize() and finally?

Final : final keyword can be used for class, method and variables. A final class cannot be subclassed and it prevents other programmers from subclassing a secure class to invoke insecure methods. A final method can’t be overridden. A final variable can’t change from its initialized value.

Finalize() : finalize() method is used just before an object is destroyed and can be called just prior to garbage collection.

Finally : finally, a key word used in exception handling, creates a block of code that will be executed after a try/catch block has completed and before the code following the try/catch block. The finally block will execute whether or not an exception is thrown. For example, if a method opens a file upon exit, then you will not want the code that closes the file to be bypassed by the exception-handling mechanism. This finally keyword is designed to address this contingency.



If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
