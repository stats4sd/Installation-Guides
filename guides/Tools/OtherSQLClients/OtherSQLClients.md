---
author: Stats4SD
...

# Other SQL Clients

Heidi is only one out of many possible clients. We recommend it as a good place to start if you have never used SQL before, but there are also other options that are more suited to particular tasks. This list is a few that the Stats4SD has some experience with that might be of interest.

## DBForge
(download here)[https://www.devart.com/dbforge/mysql/studio/download.html] - Express is the free version of the software. Other versions offer a trial version, which expires after 30 days.

DBForge is made of a set of different tools for interacting with your databases. From the start screen, there are tabs that show you these tools. Two features make DBForge a very useful tool to explore - the Query Builder (under SQL Development tab) and the Database Diagram (under Database Design tab).

###positive
The main reason to use DBForge is for the visual representation of data structures and queries.

- The Database Diagram tool lets you view your tables on a diagram, and create relationships by dragging lines between your tables. Many people will find this more intuitive than creating the relationships by manually adding foreign key constraints through Heidi.

- The visual Query builder lets you pull in fields from different tables. It automatically suggests joins to use based on the relationships present between the tables.

We have a seperate document that gives more details on the use of these tools within DBForge.

###negative
The free version of the tool is quite limited - it only allows a maximum of 10 database objects (e.g. tables) within a database diagram, and only 3 within the visual query builder. There are other restrictions compared with their paid versions, shown (on their website)[https://www.devart.com/dbforge/mysql/studio/editions.html]. The paid versions start at USD 150 per licence.

The other core functions, like importing / exporting data, making table edits etc are also not as intuitive as other packages.

DbForge only works for MySQL databases, but the company do offer applications specific to other SQL types. They currently offer apps for [Postgresql](https://www.devart.com/dbforge/postgresql/), [MS SQL Server](https://www.devart.com/dbforge/sql/) and [Oracle](https://www.devart.com/dbforge/oracle/).

**Editor's Note**
I think the main reason to use dbForge is for the database designer. Being able to map your tables visually is a huge help, and I do it for every database I design. Normally, I just sketch out the diagram on paper, or using a tool like (Draw.io)[https://www.draw.io/]. But sometimes it is nice to be able to create the diagram in the same place as your actual data, and then have the ability to create the links directly into your database, which is where dbForge is useful.

## MySQL Workbench
This is the client that comes bundled with MySQL. If you've used the [MySQL Installer from Oracle](https://dev.mysql.com/downloads/installer/) you may have seen that there's an option to also install Workbench.

###positive
- It's well supported, as it is one of the more widely used clients.
- It has a lot of functionality - you can do most things you can think of with a MySQL database through the client. It has a large array of tools that make it useful for database administration, management and development.
- It has a diagramming tool to allow you to create professional looking EER diagrams.
- If you learn how to use its design and modelling tools well, it can be a powerful part of your workflow.

###negatives
- With great power comes great complexity. While its often considered the 'default' client, it's actually one of the harder ones to learn and understand, especially for people new to SQL. 
- The diagramming tool is especially confusing for beginners, as it's not obvious how to get the changes you make to the diagram reflected in the actual database (for example, adding relationships). To use it well requires an understanding of 'forward' and 'reverse' engineering in terms of database development.
- It only works for MySQL databases.

**Comments**
This client is only recommended for more technical users, who are already familiar with MySQL. Even advanced users may find other clients to be a better choice in many situations.

##PgAdmin
PgAdmin is one of the most popular clients for PostgreSQL. It's powerful and runs on Windows, Mac or Linux.

###positive
- Very popular; has a large user base and active community support.
- It's open source and available on any platform. 
- It can be installed on a server if needed.
- It's very stable.

###negative
- Many of the dialogues for common tasks are not very intuitive.
- It doesn't include a very good code editor for scripting.
- It only supports PostgreSQL

**Comments:**
It is harder to find good, free clients for PostgreSQL compared with MySQL. For this reason, PgAdmin could be a good option if you need to use PostgreSQL and have a limited budget. Heidi does support PostgreSQL, but only in a limited way, and it is not recommended for that purpose. Table Plus does support PostgreSQL, but the Windows version is still in development.

## Table Plus
(download Windows version)[https://tableplus.io/windows]
(download Mac version)[https://tableplus.io/]

This is a relatively new application - the Mac version was released in 2017 and the Windows version was released in Summer 2018.

The full version costs $49 for a perpetual licence. There is a free-forever version, and the only restriction is that you can only have 2 sessions, with 2 tabs each, open at the same time.

The company have a '[getting started guide](https://tableplus.io/blog/2018/04/getting-started-with-tableplus.html)' that provides instructions on performing some common tasks, such as creating a connection to a database, viewsing and editing data, running queries, and importing and exporting data from CSV files.

###positive
- It works with MySQL and PostgreSQL.
- The interface is clear and clean. It's easy to see your tables, views and data.
- The SQL code editor is very nice, with autocompletion for database and object names.
- The Free version has few limitations compared to the paid version. The main limitation is in the number of tabs you can have open at a time. (The free version is limited to 2 tabs).
- It works well for both MySQL and PostgreSQL databases.

###negative
- As it's still new, it's missing some features that other SQL clients have, and it is not yet as stable and reliable as more established clients.
- It has no visual query or relationship builder.
- There is no easy way to visualise your data structures - you can view each table individually, but not all together.

-
**Comments**
Table Plus is definitely a "Mac-first" package. As of January 2019, there are a lot of features that have not yet been added to the Windows version. The development team are adding features quickly, so it's likely that the Windows version will catch up within the next year or so.

Overall, Table Plus is only recommended if you are a Mac user, or if you are already familiar with SQL and want to test out a new client.

