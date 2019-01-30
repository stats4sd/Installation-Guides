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


# How to Install {#install}

## Windows

### Download the .msi installer from the downloads page:

  [Download the MySQL Installer](https://dev.mysql.com/downloads/installer/){:target='_blank'}

- We recommend downloading the larger file (~310MB). This is a much larger download, but once downloaded will run offline. The smaller download requires an active internet connection during the installation process.
- If downloading from the [dev.mysql.com](http://dev.mysql.com) site, you'll be asked to log in or sign up. This is not required! There's an option below the buttons to just continue the download.


  ![image](/assets/images/MySQL/begin-your-download.png){:class='size--large'}

Screenshot of download page. I missed this button for years and had to log in every time I downloaded something...

### Run the installer

- It gives you the option to install lots of components, many of which you do not need. We recommend using the "Developer Default" setup type. This will install all the required components, including the actual server, and a set of connectors for different software packages.

  ![image](/assets/images/MySQL/mysql-installer-choose-components.png){:class='size--large'}

- Some products have specific requirements. For example, the Python connector requires Python to be installed, and the MySQL for Visual Studio requires Visual Studio. If you do not have something installed, you may see a "Check Requirements" screen, showing the products that cannot be installed. This is fine, as you only need these connectors if you use the relevant tools. You can safely click next past this screen.
- At the Installation screen, check the list of products to be installed. Make sure you have at least:
  - MySQL Server.
  - MySQL Shell
  - Connector/ODBC
  - Connector/C++
  - Connector/NET
- Click "Execute" to install the components.

### Configure Installed Products

Once installed, the installer will prompt you to configure some of the components. To configure the server, follow the instructions on screen:

- At Group Replication, choose "Standalone MySQL Server / Classic MySQL Replication".

![image](/assets/images/MySQL/group-replication.png){:class='size--large'}

---

- At Type and Networking, choose "Development Computer" and keep all the defaults for Connectivity.
- You do not need to 'Show advanced and logging options', as the defaults are sufficient for most installations.

![image](/assets/images/MySQL/type-and-networking.png){:class='size--large'}

---

- For **Authentication Method**, choose "Use Legacy Authentication".

![image](/assets/images/MySQL/authentication-method.png){:class='size--large'}

> **NOTE:** This is not the ideal setting in the long term. Currently, some MySQL clients do not work with the new password encryption methods introduced in MySQL 8.0. MySQL offers a 'legacy' authentication mode to allow these tools to continue to work until they're updated. If / when tools like Heidi gain support for the new authentication method, we will update this guide.

---

- For the **Accounts and Roles Page**, enter a strong root password. 
- **Make sure you remember this password!**


![image](/assets/images/MySQL/accounts-and-roles.png){:class='size--large'}

> **Good Practice Recommendation:** The root user is always the first user created on a server. It acts as the primary administration account, and always has full permissions. We recommend that for most of your work you **do not use this account!** Instead, it's good practice to create a second account that you can use. In the screenshot above, I've created a DB Admin account.
>
>While this is not strictly needed, especially on a local server where you are likely to be the only person accessing the server, it's good practice to only use your root account for server updates.
>
>You can create a new user for yourself on the Accounts and Roles config page. 
>![image](/assets/images/MySQL/create-new-user.png){:class='size--large'}
>
>You can also create an account later, through the command line or via an SQL client like Heidi.
>
>Even though you will not log in as **root** regularly, it is very important to keep that password saved somewhere, as you will need **root** for user management, creating new databases and other server-level tasks in the future.

- For **Window Service**, keep all the defaults:

![image](/assets/images/MySQL/windows-service.png){:class='size--large'}

---

- Finally, click 'execute' to apply the changes and configure the server. The server will begin automatically afterwards, and will begin automatically as a Windows Service in future when you start your computer.

---

### Configuring Other Products
You may also be asked to configure other products, such as the documentation and example databases if you chose to install them. Follow the instructions to configure the remaining products, then finish the installer.

### Installing Additional Components
You may find that, after the initial installation, you need to install additional components, for example the MySQL to Excel plugin, or the plugin for Visual Studio. You can do this by running the MySQL Installer again. 

![image](/assets/images/MySQL/mysql-installer-add.png){:class='size--large'}

When you run the installer again, you'll see a list of the components you already have installed, and different options to the right:
 - Add: Click to install new components
 - Modify: Click to reconfigure exiting components. This will take you through any post-installation setup steps for your chosen components.
 - Upgrade: This will check for updates to your installed components, and guide you through installing them if there are any available.
 - Remove: This lets you uninstall one or more components.

To add a new component, click the Add button. You will be presented with a list of available components. You may need to drill down through many levels to find the product you need. For example, The MySQL for Excel plugin is under Applications -> MySQL For Excel -> MySql For Excel 1.3 -> MySQL For Excel 1.3.7 - X86. (This might change in future versions!)

![image](/assets/images/MySQL/mysql-installer-choose-components.png){:class='size--large'}

# Further References {#references}

- [MySQL Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/){:target='_blank'}

The Reference manual itself is huge, so here are a few specific sections that may be of use:
- [Installing MySQL on Windows](https://dev.mysql.com/doc/refman/8.0/en/windows-installation.html){:target='_blank'} - This provides more in-depth notes about the various options available at install time.
- [Tutorial - Using MySQL via the Command Line](https://dev.mysql.com/doc/refman/8.0/en/tutorial.html) - This tutorial is recommended for advanced users who want to interact with mySQL via the command line or through scripts.