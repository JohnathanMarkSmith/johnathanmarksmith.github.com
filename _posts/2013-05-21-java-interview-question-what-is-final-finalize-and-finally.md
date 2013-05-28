---
layout: post
title: "Java Interview Question: What is final, finalize() and finally"
description: "Java Interview Question: What is final, finalize() and finally"
categories: [ Java, Java Interview Questions ]
tags: [ Java, Java Interview Questions ]
comments: false
---

   Final : final keyword can be used for class, method and variables. A final class cannot be subclassed and it prevents other programmers from subclassing a secure class to invoke insecure methods. A final method can’t be overridden. A final variable can’t change from its initialized value.

   Finalize() : finalize() method is used just before an object is destroyed and can be called just prior to garbage collection.

   Finally : finally, a key word used in exception handling, creates a block of code that will be executed after a try/catch block has completed and before the code following the try/catch block. The finally block will execute whether or not an exception is thrown. For example, if a method opens a file upon exit, then you will not want the code that closes the file to be bypassed by the exception-handling mechanism. This finally keyword is designed to address this contingency.


   You can see the full list of <a href="/java-interview-questions.html">Java Interview Questions Here</a>

   If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


{% include JB/setup %}
