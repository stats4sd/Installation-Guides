---
layout: default
section: Guides
title: Database Setup
permalink: /concepts/database-setup
---

# Database Setup

## Terminology
These terms are very useful to know, and will help your overall understanding of how MySQL (and other database systems) actually work.

**MySQL Server**: The actual installation of MySQL. This runs in the background, either on your local computer or on a remote server. You can interact with the server through the command line (a shell terminal), or through an SQL Client.

**Database:** A MySQL database is a set of tables, views, functions and other objects. A MySQL Server typically hosts multiple databases. Users can be given different permissions on different databases, so you can control who can access which databases. This allows you to keep databases for different projects or purposes on the same SQL Server.

**Client:** A piece of software that lets you connect to a server. Clients generally let you configure multiple connections, so you can connect to your local server, or a remote server, through the same client. Examples of SQL clients are Heidi, MySQL Workbench and DBForge.

It is very useful to understand the difference between these 3 concepts. When you "install MySQL" onto your computer, you're installing the MySQL **server**. You then use a **client** to access that server, and create one ore more **databases** for your projects.

![image](/assets/images/MySQL/Screenshot2018-10-2212-b6509f08-cad9-4e2b-a443-95bce75ee2b5.13.27.png)

**User Account:** To access a server and the databases it hosts, you need a user account, which consists of a username and password. To read, alter, delete or update anything in a database, a user needs to be given permissions to do so. Permissions can be given at the database level, or globally.


## Good Practice

### The Root User Account
When you first install a mySQL server, a root user will be created. This root user has full access to every database on the server, so it should be protected with a secure password. Anyone with 'root' access can see, edit and delete anything on your server, so make sure only your data manager(s) have access to this account. 

Given its power to create and destroy, the root user should only be used if needed, for example when setting up a new database for a project. Ideally, no-one should use the root user as their main account - even the Data Manager! You can create a seperate account, and give that account the needed permissions on each database, to use for day-to-day activities.

Why? Because then the root user can be reserved for emergencies, or for specific tasks like creating new databases for a project. For this reason, we recommend that at least 2 people have access to the root user account credentials. These people may never use them, but this means that you don't have a single person in your project with all the admin passwords.

It is possible that your team only has 1 data manager - you. In this case, you may not want anyone else logging in as the root user and messing around - this is very sensible, as you want to make sure that an untrained person doesn't accidentally delete something. But, even here, it's a good idea to have the root user credientials saved somewhere so that someone else in your project can, in an emergency, get access to them. Be careful to save them securely - perhaps investigate a password manager like [Dashlane](https://www.dashlane.com/), [1Password](https://1password.com/) or [KeePass](https://keepass.info/). Hopefully, your colleagues will never need them, but if they do, they'll be grateful you saved them somewhere reachable.

### Other User Accounts
We recommend that everyone who will need access to your server gets assigned a user account. This serves 2 purposes:

1. You can assign permissions on a per-user basis. For example, you could let your PI view all data within both your raw and cleaned database tables, but they do not need to create or update records, as that's your job.
2. It makes it easier to track who is accessing your data, and if you have logging setup, you can also see who is making changes.

If you're just working locally, you still need an account for yourself, and it's a good idea to think a bit about what permissions you chould assign yourself. What will you be doing on a daily basis? If you're not regularly creating new databases or deleting old ones, maybe don't give yourself those permissions - this can prevent accidents later on!

If you are working with a remote server, it's likely that you'll want multiple users or groups to access your database. At this point, user management becomes very important, and we suggest spending some time getting to know what permissions are available in MySQL so you can correctly assign them. Most clients will have a section where you can see and edit all the users on the server.
