---
title: Lambda Labs Week IV/ Payme Application , Set up REMINDERS  API
date: "2019-05-18T09:15:37.121Z"
description: This post is going to showcase Reminders' Apis, the front-end client should be able to Send,Save,Retrieve reminders and get all created invoices.
---
In this post, i will go through all the major steps needed to build a secure API.
You can check the full code developed throughout this post [in this GitHub repository.](https://github.com/Lambda-School-Labs/labspt2-pay-me)

Below is the dataflow chart of our developed  RESTful APIs  :

![dataflow file](https://i.imgur.com/W87zeoY.jpg)


### I. Let's look at the API we want to build 

Our Api will Handle 3 CRUD operations on our database and will consume 2 third party Api( SendGrid APi and Nexmo API ):
* Get all invoices (GET)
* Save reminders (POST)
* and view reminders (GET)
* and finally it will allows clients to send Email and Sms.(POST)
![dataflow file](https://i.imgur.com/EG30kWV.jpg)


### II. The incredible TaskManager 

The diagram below shows the 4 functions which will handle all requests between the client and the server.
![TaskManager](https://i.imgur.com/pILtjqy.png)

to be continued... (by tommorow)

Conclusion:

In this post i did a brief description of how to set ....
