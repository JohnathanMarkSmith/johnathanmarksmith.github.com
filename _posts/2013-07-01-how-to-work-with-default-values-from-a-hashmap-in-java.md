---
layout: post
title: "How to work with Default Values from a HashMap in Java"
description: "How to work with Default Values from a HashMap in Java"
categories: [ Java, Programming]
tags: [ Java, Programming]
comments: false
---

This is a quick example on how to get default values in hashMaps and other java objacts.

Here is the source code:

        public class App {
            public static void main(String[] args) {
                System.out.println("Hello World, Default Values In HashMap Example" );

                Map<String, String> myMap = new HashMap<String, String>();

                myMap.put("SABRAIN", "KID");
                myMap.put("JESSCIA", "KID");
                myMap.put("JOHNATHAN","ME");

                Iterator iterator = myMap.entrySet().iterator();

                /**
                 *
                 *   This will show all the keys and values in my hashMap
                 */
                while (iterator.hasNext()) {
                    Map.Entry mapEntry = (Map.Entry) iterator.next();
                    System.out.println("The key is: " + mapEntry.getKey()
                            + ",value is :" + mapEntry.getValue());
                }

                /**
                 *
                 * Now lets look for someone not in the map and setup a default value
                 *
                 */

                System.out.println(StringUtils.defaultString(myMap.get("REGAN"),"WIFE"));


            }
        }


You need to add this to your POM

          <dependency>
              <groupId>org.apache.commons</groupId>
              <artifactId>commons-lang3</artifactId>
              <version>3.0</version>
          </dependency>



checkout the project from github.

    git clone git@github.com:JohnathanMarkSmith/DefaultValuesInHashMap.git
    cd DefaultValuesInHashMap
    mvn package
    cd target
    java -jar DefaultValuesInHashMap.jar


If you have any questions or comments please email me at john@johnathanmarksmith.com or checkout my web site http://JohnathanMarkSmith.com


{% include JB/setup %}
