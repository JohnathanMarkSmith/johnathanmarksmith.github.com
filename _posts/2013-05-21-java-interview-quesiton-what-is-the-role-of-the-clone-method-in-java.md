---
layout: post
title: "Java Interview Quesiton: What is the role of the clone() method in Java"
description: "Java Interview Quesiton: What is the role of the clone() method in Java"
categories: [ Java, Interview Questions ]
tags: [ Java, Interview Questions ]
comments: false
---

Protected Object clone() throws CloneNotSupportedException.

This method is used to create a copy of an object of a class which implements Cloneable interface.

By default it does field-by-field copy as the Object class doesn’t have any idea in advance about the members of the particular class whose objects call this method. So, if the class has only primitive data type members then a completely new copy of the object will be created and the reference to the new object copy will be returned. But, if the class contains members of any class type then only the object references to those members are copied and hence the member references in both the original object as well as the cloned object refer to the same object.


You can see the full list of <a href="/java-interview-questions.html">Java Interview Questions Here</a>

If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
