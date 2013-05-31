---
layout: post
title: "How To Use JQuery BeautyTips (ToolTips) and Validation Plugins for Frield Validatoin"
description: "How To Use JQuery BeautyTips (ToolTips) and Validation Plugins for Frield Validatoin"
categories: [ JQuery, JavaScript ]
tags: [ JQuery, JavaScript ]
comments: false
---

### JQuery ToolTips and Validation Example

This is just a one JSP page example that demos some JQuery ToolTips and Validation stuff.  Yes I really did not have to use a JSP and tomcat7 but again this is only a one page example so why not... :)

in my example I have some HTML code that looks like the following:

        <div>
            <form id="myForm">
                <p>
                    Gender:
                    <label for="male">Male</label>
                    <input type="radio" name="gender" id="male" class="target" title="Please enter your gender.">
                    <label for="female">Female</label>
                    <input type="radio" name="gender" id="female" class="target" title="Please enter your gender.">

                </p>
                <p>
                    <label for="firstName">First Name:</label>
                    <input id="firstName" name="firstName" class="target" title="Please enter your first name." ></input>
                </p>
                <p>
                    <label for="lastName">Last Name:</label>
                    <input id="lastName" name="lastName" class="target" title="Please enter your last name." ></input>
                </p>
                <p>
                    <label for="age">Age:</label>
                    <input id="age" name="age" class="target" title="Please enter your age." ></input>
                </p>
                <p>
                    <input type="submit" value="Submit" />
                </p>
            </form>
        </div>

I wanted to put some validation in to check that data was entered into the fields and why not use JQuery for it..

I then made the following style sheet code:

            <style type="text/css">
                    #errorContainer {
                        display: none;
                        overflow: auto;
                        background-color: #FFDDDD;
                        border: 1px solid #FF2323;
                        padding-top: 1;
                    }

                    #errorContainer label {
                        float: none;
                        width: auto;
                    }

                    input.error {
                        border: 1px solid #FF2323;
                    }

             </style>


This is going to setup how the errors will look.  I then had to add a place on my page for the errors so I added the following div:

        <div id="errorContainer">
            <p>&nbsp;Please correct the following errors and try again:</p>
            <ul />
        </div>

The above code is where JQuery will be displaying the errors.

### Now its time for the HARD work :)

You need to add the JQuery, BeautyTips (ToolTips) and the Validate libs into your code by added the following lines:

        <script type="text/javascript" src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.7.2.min.js"></script>
        <script type="text/javascript" src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.9/jquery.validate.min.js"></script>
        <script src="js/jquery.bt.min.js" type="text/javascript" charset="utf-8"></script>

Now lets add the JQuery/JavaScript code that will check the fields on the page.  As you can see from the code below I give JQuery the rules which is (field names, ranges) and the error messages to display.


        <script type="text/javascript">
            $(function(){

                $('#myForm').validate({
                    rules: {
                        firstName: "required",
                        lastName: "required",
                        age: {
                            required: true,
                            range: [18,70]
                        }
                    },
                    messages: {
                        firstName: "Please enter your first name.",
                        lastName: "Please enter your last name.",
                        age: {
                            required: "Please enter your age.",
                            range: "Your age must be between 21 and 55."
                        }
                    },
                    errorContainer: $('#errorContainer'),
                    errorLabelContainer: $('#errorContainer ul'),
                    wrapper: 'li'
                });

            });
        </script>


Now test your code.. It works great but where are the tooltips?

### Adding BeautyTips (Tooltips)

Rewrite the javascipt code with the code below:

    <script type="text/javascript">
        $(function(){

            $('#firstName').bt();
            $('#lastName').bt();
            $('#age').bt();
            $('#male').bt();
            $('#female').bt();

            $('#myForm').validate({
                rules: {
                    firstName: "required",
                    lastName: "required",
                    gender: "required",
                    age: {
                        required: true,
                        range: [18,70]
                    }
                },
                messages: {
                    firstName: "Please enter your first name.",
                    lastName: "Please enter your last name.",
                    gender: "Please enter your gender.",
                    age: {
                        required: "Please enter your age.",
                        range: "Your age must be between 21 and 55."
                    }
                },
                errorContainer: $('#errorContainer'),
                errorLabelContainer: $('#errorContainer ul'),
                wrapper: 'li'
            });

        });
    </script>

you can see all that we added was:

    $('#firstName').bt();
    $('#lastName').bt();
    $('#age').bt();
    $('#male').bt();
    $('#female').bt();

The above code tells Beautytips to add the tooltips


You can see how easy it is to use JQuery, BeautyTips(ToolTips) and Validation...


### How To Get The Project and Run It

checkout the project from github.

    git clone git@github.com:JohnathanMarkSmith/JQueryToolTipValidation.git
    cd JQueryToolTipValidation
    mvn tomcat7:run

Then open http://localhost:8080/JQueryToolTipValidation.git/ in your browser and play around.. Go have fun....

You can download the source code to this at my github project (https://github.com/JohnathanMarkSmith/JQueryToolTipValidation)


If you have any questions please email me at john@johnathanmarksmith.com


{% include JB/setup %}
