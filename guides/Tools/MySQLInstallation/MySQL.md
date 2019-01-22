---
layout: default
section: Tools
title: MySQL
permalink: /tools/mysql
---

# MySQL

# What is it? {#what}

MySQL is a database server and a language that allows you to interact with databases.

It can be installed on your local machine or a remote server / cloud server. If you are going to do any work with MySQL, we recommend installing it locally so you can work and test your code in a safe, offline environment. Even if your main databases will only exist on a remote server, we recommend having a local SQL database setup so you can practice and test your code while offline.

# Why use it? {#why}

- It's is a very popular version of SQL (Structured Query Language), so there are a lots of tools and systems that can interact with a MySQL database.
- It's free and open source.
- It's considered easier to learn than other SQL systems like PostgreSQL or MS SQL.

For a more general disucssion on when to use a database system instead of a collection of Excel files, see the 

# Terminology

**MySQL Server**: The actual installation of MySQL. This runs in the background, either on your local computer or on a remote server. You can interact with the server through the command line (a shell terminal), or through an SQL Client.

SQL **Client:** A piece of software that lets you connect to a MySQL server. Clients generally let you configure multiple connections, so you can connect to your local server, or a remote server, through the same client. Examples of SQL clients are Heidi, MySQL Workbench and DBForge.

**Database:** A MySQL database is a set of tables, views, functions and other objects. A MySQL Server typically hosts multiple databases. Users can be given different permissions on different databases, so you can control who can access which databases. This allows you to keep databases for different projects or purposes on the same SQL Server.

**User Account:** To access a server and the databases it hosts, you need a user account, which consists of a username and password. To read, alter, delete or update anything in a database, a user needs to be given permissions to do so. Permissions can be given at the database level, or globally.

# How to Install

## Windows

1. Download the .msi installer from the downloads page:

[MySQL :: Download MySQL Installer](https://dev.mysql.com/downloads/installer/)

- We recommend downloading the larger file (~310MB). This is a much larger download, but once downloaded will run offline. The smaller download requires an active internet connection during the installation process.
- If downloading from the [dev.mysql.com](http://dev.mysql.com) site, you'll be asked to log in or sign up. This is not required! There's an option below the buttons to just continue the download.

![image](/assets/images/MySQL/Screenshot2018-10-2212-b6509f08-cad9-4e2b-a443-95bce75ee2b5.13.27.png)

Screenshot of download page. I missed this button for years and had to log in every time I downloaded something...

2. Run the installer.

- It gives you the option to install lots of components, many of which you do not need. We recommend using the "Developer Default" setup type. This will install all the required components, including the actual server, and a set of connectors for different software packages.

![image](/assets/images/MySQL/Screenshot2018-10-2212-5823a41e-c3a1-46fa-9b02-79f43a08750c.20.03.png)

- Some products have specific requirements. For example, the Python connector requires Python to be installed, and the MySQL for Visual Studio requires Visual Studio. If you do not have something installed, you may see a "Check Requirements" screen, showing the products that cannot be installed. This is fine, as you only need these connectors if you use the relevant tools. You can safely click next past this screen.
- At the Installation screen, check the list of products to be installed. Make sure you have at least:
  - MySQL Server.
  - MySQL Shell
  - Connector/ODBC
  - Connector/C++
  - Connector/NET
- Click "Execute" to install the components.
- Once installed, the installer will prompt you to configure some of the components. To configure the server, follow the instructions on screen:

- At Group Replication, choose "Standalone MySQL Server / Classic MySQL Replication".

![image](/assets/images/MySQL/Screenshot2018-10-2212-42bbc595-7b80-46a2-b33c-c4ff33e4ecfb.28.05.png)

---

- At Type and Networking, choose "Development Computer and keep all the defaults for Connectivity.
- Tick "Show Advanced and Logging Options" so you can choose where to store the log files in a later step.

  ![image](/assets/images/MySQL/Screenshot2018-10-2212-1c454a37-5711-47c5-b908-3d75ba5a627f-86322c70-a6d5-4cae-8a4b-f369d9bb31b9.28.22.png)

---

- For **Authentication Method**, choose "Use Legacy Authentication".

![image](/assets/images/MySQL/Screenshot2018-10-2212-cb4b4b0c-a34b-4113-b546-049bfb4a707e.34.57.png)

---

- **NOTE:** This is not the ideal setting in the long term. Currently, some MySQL clients do not work with the new password encryption methods introduced in MySQL 8.0. MySQL offers a 'legacy' authentication mode to allow these tools to continue to work until they're updated. If / when tools like Heidi gain support for the new authentication method, we will update this guide.
- For the **Accounts and Roles Page**, enter a strong root password. Make sure you remember this password!

![image](/assets/images/MySQL/Screenshot2018-10-2212-b6928504-09e4-4b07-b311-4ae03ecbbb24.29.51.png)

---

- **Good Practice Recommendation:** The root user is always the first user created on a server. It acts as the primary administration account, and always has full permissions. We recommend that for most of your work you **do not use this account!** Instead, it's good practice to create a second account that you can use. In the screenshot above, I've created a DB Admin account.

  While this is not strictly needed, especially on a local server where you are likely to be the only person accessing the server, it's good practice to only use your root account for server updates.

  You can create a new user for yourself on the Accounts and Roles config page. You can also create an account later, through the command line or via an SQL client like Heidi.

- For **Window Service**, keep all the defaults:

  ![image](/assets/images/MySQL/Screenshot2018-10-2212-d9b171db-d7b2-486a-9b5d-4569beaeee92-d21254a8-5b81-445f-a04a-9d6ddf8922de.30.02.png)

---

- For Logging Options: our recommendation is to enable the Slow Query log and the Bin log. Either keep the default names or choose a different file path. Even if you don't want to change the path, click the 3-dots next to one of the file names to see where the logs will be stored. You can exit the dialog without entering a new name by clicking cancel.

  ![image](/assets/images/MySQL/Screenshot2018-10-2213-d83449df-f392-423b-b1c0-8749087d4a3f-3a551f23-8778-4378-9f15-20db482e9f63.45.45.png)

---

- For Advanced Options: keep all the defaults.

  ![image](/assets/images/MySQL/Screenshot2018-10-2212-c373581c-d5dd-4e02-bca4-4599e761c348-4b36b60d-f0b0-4dae-b880-3c0b3c32aaf9.31.31.png)

---

- Finally, click 'execute' to apply the changes and configure the server. The server will begin automatically afterwards, and will begin automatically as a Windows Service in future when you start your computer.

---

You may also be asked to configure other products, such as the documentation and example databases if you chose to install them. Follow the instructions to configure the remaining products, then finish the installer.

### Installing Additional Components
You may find that, after the initial installation, you need to install additional components, for example the MySQL to Excel plugin, or the plugin for Visual Studio. You can do this by running the MySQL Installer again. 

![image](/assets/images/MySQL/mysql-installer-add.png)

When you run the installer again, you'll see a list of the components you already have installed, and different options to the right:
 - Add: Click to install new components
 - Modify: Click to reconfigure exiting components. This will take you through any post-installation setup steps for your chosen components.
 - Upgrade: This will check for updates to your installed components, and guide you through installing them if there are any available.
 - Remove: This lets you uninstall one or more components.

To add a new component, click the Add button. You will be presented with a list of available components. You may need to drill down through many levels to find the product you need. For example, The MySQL for Excel plugin is under Applications -> MySQL For Excel -> MySql For Excel 1.3 -> MySQL For Excel 1.3.7 - X86. (This might change in future versions!)

![image](/assets/images/MySQL/mysql-installer-choose-components.png)