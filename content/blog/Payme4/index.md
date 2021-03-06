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


### III. Reminders data process
![Reminders_process](https://i.imgur.com/5rjsR2J.jpg)

* Get Invoices function

-- This function will handle all request send to api/reminders/invoice/:userId endpoint.
![GetInvoices](https://i.imgur.com/5pQDcI3.jpg)
The output data format will be for each invoice data, we will be joining the corresponding client and user data via foreign keys that linked all tree tables. 

-- The response data will be a json object with all informations needed by the front-end reminders forms such as Invoice Number, User contact information and Client contant information.

* Send Reminders function

-- once the GetInvoices status succeded ,the front-end user can fill all required fields of our reminders' form and send a Post request to  api/reminders/send, below is a half shootscreen :
![send reminders](https://i.imgur.com/M8Pf4KO.jpg)

-- SendReminders will extract the Request Body , get all needed parameters and handle them to the appropriate module.

-- We will be using TimerJOb npm module to Create timers that can run often. Great for our reminders, the front-end user will pick a data-time  when to start the TimerEmail and/or the TimerSms(handled by a simple setTimeout function) and and then repeat sending the same email/sms periodically.
![send reminders](https://i.imgur.com/ZNKYYjr.jpg)
[Learn more about TimerJOB](https://www.npmjs.com/package/timer-jobs).

-- SetToHappenOn function will call TimerEmail and TimerSms on a Start Date set by the front-end user,

-- TimerEmail/TimerSms will execute emailData/smsData often time (Email Freq/ Sms Freq) and this last will keep sending email/sms reminders via sendGrid APi/Nexmo Api;

In my next post will knockout all requirements how to get started with sendGrid APi/Nexmo Api.

We had a Team Zoom meeting and figured out how to set a feedback to the Front-end User to let him know that the reminder was successful sent to his client and we decided to save (a POST to /API/REMINDERS/SAVE) each reminder sent and send back a feedback from the our server (GET to /API/REMINDERS/VIEW).


Conclusion:

In this post i did a brief description of how to buil a REST API that allows Users to send Email and Sms reminders to their clients.
![received sms reminders](https://imgur.com/O3WpHs6.jpg)
![received email reminders](https://imgur.com/rsySUjO.jpg)

This was an interresting feature to build and i faced many obstacles but at the end i was filled with joy to look over my Gmail box and Phone and find an email reminders and sms reminder (text message) .

Thanks for taking you  time to read this post, check the next topic !!!
