---
layout: page
title: "Java Interview Questions"
description: "Java Interview Questions"
---

## Java Interview Questions

After over 25 years I still don't like going on interview and getting asked questions that a good programmer/developer dont have to know off the top of his/her head. I good programmer/developer should NOT know all the anwsers but should know how to find them and where to search.  

I am posting this page so programmers/developers can bookmark it and use it.  I am going to be posting some questions that I think everyone will ask.  If you have any questions that I am missing please email me.

# The Java Questions

## In Java, what’s the difference between method overloading and method overriding?

 The difference between overriding and overloading in Java is a common source of confusion – but it is fairly simple to understand. Let’s start the discussion by talking more about method overloading. Overloading in Java can occur when two or more methods in the same class share the same name or even if a child class shares a method with the same name as one of it’s parent classes. But, in order to actually have overloaded methods, the methods not only have to have the same name, but there are other conditions that must be satisfied – read below to see what those conditions are.

Suppose we have a class called TestClass which has 2 methods, and both methods have the same name – let’s say that name is “someMethod” – this would be considered to be method overloading if at least one of these 2 things is true:

    1.) The number of parameters is different for the methods   
    2.) The parameter types are different.  

How to NOT overload methods:

It’s important to understand that method overloading is NOT something you can accomplish by doing these 2 things:

    1.) Changing the return type of the method   
    2.)  Changing the name of the method parameters, but not changing the parameter types.  

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




If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

{% include JB/setup %}
