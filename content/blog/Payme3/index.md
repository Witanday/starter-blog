---
title: Lambda Labs Week III/ Payme Application , Building reminders -Backend/Node-Express-Knex-Sqlite3
date: "2019-04-24T09:15:37.121Z"
description: In this topic i will describe how i proceeded to build the basic components for the backend 
---
I won't describe  how to install  Node ,  Express, knex and sqlite,i'm assuming all features have already been installed and the server set up,I'll point out (1)Quick definitions, (2)How to set KnexFile (3)Migrations and Seedings ,below is the screenshot of our server file structure:
![server file](https://i.imgur.com/5r9jZaR.jpg)


### I. Quick definitions .
I will start out by briefly introducing Node , Express, knex and sqlite
* Node.Js : out from wikipedia.com,Node.Js represents a "JavaScript everywhere" paradigm, unifying web application development around a single programming language, rather than different languages for server side and client side scripts.[learn more on NodeJs](https://en.wikipedia.org/wiki/Node.js)
* Express.js: Express is a minimal, open source and flexible Node.js web app framework designed to make developing websites, web apps, & API’s much easier. ...[learn more on ExpressJs](https://expressjs.com/);
* SQLite :is the most used database engine in the world. SQLite is built into all mobile phones and most computers and comes bundled inside countless other applications that people use every day.[learn more on Sqlite3](https://en.wikipedia.org/wiki/Node.js)
* KnexJs: Knex is a SQL query builder, mainly used for Node.js applications with built in model schema creation, table migrations, connection pooling and seeding. we will use Knex to query our Sqlite3 database.[learn more on KnexJs](https://knexjs.org/)
* PostgreSQL:  is a general purpose and object-relational database management system, the most advanced open source database system.[learn more on PostgreSQL](https://www.postgresql.org/)
### II.How to set KnexFile
* Using our command terminal , we navigate in our Server folder and run this command : "Knex init" this will create a knexfile.js  which will act as our configuration for different environments(here development point to Sqlite3 and production point to Postgresql), we the generated content Knexfile.js with: 
![knexfile](https://i.imgur.com/g4Zphrc.jpg)
Migrations and Seed files are created in the directory specified in our knexfile.js for the current environment
### III. Migrations and Seedings 

* Migrations are a way to make database changes or updates, like creating or dropping tables, as well as updating a table with new columns with constraints via generated scripts.
we run this command << knex migrate:make Name_table>> for each table (users,invoice,payment,reminders and ...)
The content of these files will stub out empty up and down functions to create or drop tables or columns.
we will use knex syntax to create and drop any table or column.
![Migration](https://i.imgur.com/g8CdKQj.jpg)
The we can run the below command performing a migration and updating our local database:
<< knex migrate:latest>>
Use << knex migrate:rollback>> to drop a table

* Seeding : As we did  for migrations, the knex module allows us to create scripts to insert initial data into our tables called seed files! If we have relations on our tables, the seeding must be in a specific order to so that we can rely on data that might already be in the database. For example, we must seed before a  table  on which other table will be join to, using foreign key.

To create a seed we run this command << knex seed:make <01-Table_name>>> for all tables
The we  insert some data into our seed scripts
![Migration](https://i.imgur.com/yCuNABf.jpg)

<< knex seed:run >> will populate our DB with our created seeds. 
* Screenshot of our Database in DB Browser for Sqlite
![Migration](https://i.imgur.com/nLqSIf3.jpg)
* Screenshot of our RemindersTable Data in DB Browser for Sqlite
![Migration](https://i.imgur.com/NKF4INc.jpg)

Conclusion:

In this post i did a brief description of how to set Knex and get ready to start make request and querying our Database,
The next post will be dedicated on building our Api for Sending Email and Sms reminders.
