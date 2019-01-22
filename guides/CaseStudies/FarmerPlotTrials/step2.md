---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Importing the raw data
permalink: /case-study/farmer-plot-trials/step-2
---

# Importing the raw data

In this step we will connect to our database directly from microsoft excel, and use it to import data into our database

## 1. Install the MySQL for Excel extension

Whilst it is possible to add csv data directly to a MySQL database, using excel provides the extra benefit of automatically detected the format of your data, defining correct column types in our table.

The MySQL for Excel extension may have automatically have been installed when you installed MySQL. You can check by opening Excel and clicking on the **Data** tab

![image](/assets/images/MySQL/mysql-for-excel-toolbar.png)

If it is not there you should open the [MySQL installer](/tools/mysql) and add the MySQL for Excel product (See the [MySQL page](/tools/mysql#InstallExtras) for details). If this still does not work you can directly download the MySQL for Excel installer <a href="https://dev.mysql.com/downloads/windows/excel/" target="_blank">here</a>

## 2. Open the raw data file in excel

Download the following file and open in excel: <a href="/assets/resources/Farmer Trials Data.xlsx" download>Farmer Trials Data.xlsx</a>

## 3. Connect to your database

If this is your first time using mysql for excel you will need to add a connection to your database.
Click on **New Connection** and complete the details in the same way as the previous step

![image](/assets/images/MySQL/mysql-for-excel-new-connection.png){:class="size--small"}

![image](/assets/images/MySQL/mysql-for-excel-new-connection-details.png){:class="size--large"}

Finally double click on the connection created to open it

![image](/assets/images/MySQL/mysql-for-excel-connections.png){:class="size--small"}

## 3. Import the data into MySQL

We will use excel to send data into our database. The first thing we need to do is create a new _schema_, essentially an object that holds information about our database.

### a. Create a schema

Click on **Create New Schema**

![image](/assets/images/FarmerTrials/create-schema-1.png){:class="size--small"}

Provide a name and set the collation as **utf8_unicode_ci**

![image](/assets/images/FarmerTrials/create-schema-2.png){:class="size--large"}

Double click the created schema to open

![image](/assets/images/FarmerTrials/create-schema-3.png){:class="size--small"}

### a. Import household info data

The first dataset we will import is the household information. You can find this on the _hh_info_ tab

Select all the data and click **Export Excel Data to New Table**

![image](/assets/images/FarmerTrials/export-data-1.png)

In the window that appears you should be able to keep most of the default settings, however as our data already has a column of _unique_ identifiers (form*ID) we can use this for our \_primary key*

![image](/assets/images/FarmerTrials/export-data-2.png)

> **IMPORTANT:** Excel will likely make some mistakes when defininng your data formats.
> Here are <a href="/resources/mysql-for-excel-tips" target="_blank">some quick tips to ensure your data maintains the correct format</a>

If successful you will see the following message
![image](/assets/images/FarmerTrials/export-data-3.png)

### b. Import plot data

We now need to repeat the process for plot data. It is the same as above except we no longer have a unique identifier, so we will let the database assign one for us:

![image](/assets/images/FarmerTrials/export-data-4.png)

![image](/assets/images/FarmerTrials/export-data-5.png)

### c. Trial preference data

Finally we repeat for the preference data received from the trial

![image](/assets/images/FarmerTrials/export-data-6.png)

![image](/assets/images/FarmerTrials/export-data-7.png)

## 4. Confirm the data is in your database

Once this is complete we should confirm the data is in our database.

Go back to heidi and click on your database. You should see a list of the tables created (if they are not there you might need to click refresh).

![image](/assets/images/FarmerTrials/export-data-8.png)

## Review and Next Step

At this stage, we have all of our data from Excel imported into our database. The data are in 3 tables, which correspond to the 3 worksheets in our Excel file.

In the [next step](/case-study/farmer-plot-trials/step-3), we will do some data cleaning and create a set of 'processed' data tables that we can use for querying.
