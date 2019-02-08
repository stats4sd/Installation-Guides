---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Cleaning the data
permalink: /case-study/farmer-plot-trials/step-3
---

# Cleaning the data

In this step we will using [OpenRefine](/tools/open-refine) to clean our trial data and repopulate our database.

If you do not have it installed you can follow the link to the tools page.

## 0. Backup the original _raw_ data

It is good practice to always retain a copy of original data in case you ever need to review or undo changes.
As such for each of our tables we will make a copy called _raw_, which we **will not ever make changes to**

For each table in your database you should _right-click_ on the table and select _Create new_ and _Table copy_

![image](/assets/images/FarmerTrials/data-backup-1.png)

This will prompt you to provide a name for you new table. It is recommend you keep the original name and add _\_raw_ to the end of the name

![image](/assets/images/FarmerTrials/data-backup-2.png){:class="size--medium"}

Repeat this process until you have backups of the raw data in all of your tables.

![image](/assets/images/FarmerTrials/data-backup-3.png){:class="size--medium"}

## 1. Create a new project in OpenRefine

When you open OpenRefine you should see the project start screen.
We will create a new project and connect to our database directly.

![image](/assets/images/FarmerTrials/open-refine-connect-to-db.png)

After a successful connection, OpenRefine shows a query editor, which allows you to specify which data to select from the database. We want all the hh_info data, so complete the query as shown: **SELECT * FROM hh_info**

![image](/assets/images/FarmerTrials/open-refine-query-db-table.png){:class="size--medium-large"}

You will see a preview of your data. Check that you have the columns you expect.

![image](/assets/images/FarmerTrials/open-refine-preview-from-db.png)

When the correct data is set and project named you can click **Create Project** to proceed

## 2. Check each column for inconsistency

One of the powers of openRefine comes from quickly identifying inconsistencies within a column of data. To do this we select the column and tell the software what type of data, or _facet_, we are expecting. For example this might be _Text_ or _Numberic_. We can then do analysis on the data.

It is good practice to look at every column of your data. For this example we will just look at a few.

### a. ngo_name

Data collectors were asked to type the name of the NGO they were working with. To analyse the results we first click on the dropdown menu next to the column header. The NGO names are a text field and so we should select the _text_ facet.

![image](/assets/images/FarmerTrials/open-refine-3.png)

You will see a new menu appear on the left, showing the different names of NGOs and how many rows of data contain each name

![image](/assets/images/FarmerTrials/open-refine-4.png)

We can see from the data that there is both the NGO 'AVENE' as well as 'avene'. This is an error.

If we hover on the name 'Avene' we will see an _edit_ button appear. Click on the button and type the correct spelling 'AVENE'.

![image](/assets/images/FarmerTrials/open-refine-5.png){:class="size--medium-large"}

When you click _Apply_ it will automatically change all the rows with the incorrect spelling, and reflect in our table summary.

Finally we can click on the close button when we have finished analysing the ngo_name column

![image](/assets/images/FarmerTrials/open-refine-6.png){:class="size--medium-small"}

### b. County

Let's repeat the process for the _county_ field. This is another _text_ facet, and has similar inconsistencies.

![image](/assets/images/FarmerTrials/open-refine-7.png)

We will use a quick method to make all the data consistently upper case.

From the same _county_ dropdown menu select _Edit cells_ then _Common transformations_ then _To uppercase_

![image](/assets/images/FarmerTrials/open-refine-8.png)

Now all of our data is written in a consitent way

![image](/assets/images/FarmerTrials/open-refine-9.png){:class="size--medium-small"}

### c. farmername

Finally we will analyse our _farmername_ column.

When the data was collected, it was expected that all farmers surveyed should have only been surveyed once. We can check this in the following way:

Apply a _text facet_

![image](/assets/images/FarmerTrials/open-refine-10.png)

Click to _sort by count_

![image](/assets/images/FarmerTrials/open-refine-11.png){:class="size--medium-small"}

We can immediately see that many of our farmers have 2 records.

> Dealing with duplicates is perhaps one of the hardest jobs of a data manager. There is often no easy way to determine which records (if any!) should be kept, and eventually you may need to simply delete all the records with duplicate IDs from your data.

In this example, we know that the duplicate records are due to enumerators visiting those farms twice at different times to collect preference data. This wasn't in the design, but it's what happened, so we have to handle it in the data.

If we keep all these duplicates in the data, then these duplicated farmers will have an unbalanced impact on the results of the study. We therefore need to do something to remove the duplicates. This gives us 2 options: 

1. Find out which records are "correct" and delete the others. This will require detailed explanation in your report to explain why you considered the "correct" records to be valid.
2. If you cannot distinguish which are the "correct" records, you should remove all the duplicates from the database.

Here, we will choose to remove all the duplicates, as it is the safer option and we do not have enough information to identify the "correct" records.

> Remember: an incomplete dataset is better than a dataset with incorrect data.

As the data in *hh_info* table is also linked with the data in the *plot_data* table, we will need to keep a log of the records we delete, so we can delete the corresponding records in the *plot_data* table before re-importing everything into the database.

### Check the duplicate records

 We do not want to include the 'other' farmername records in our list of duplicates. By looking at the data, it is clear that these are 2 different farmers. They were given the farmername 'other' because they did not have a pre-assigned farmername.

![image](/assets/images/FarmerTrials/open-refine-show-other-records.png)

>In this example, we will leave these 2 records as they are. In the future, we would ideally want to assign them a unique farmername, so we can uniquely identify them in future studies within this network.

### Isolate the duplicates for removal

To select all the duplicate records, hover over the farmernames in the facet and click **include**. 

![image](/assets/images/FarmerTrials/open-refine-include-in-selection.png)

We now have 14 selected records. Before we remove these records, we should log the form_IDs. To do this, we can export the current selection as a .csv file:

![image](/assets/images/FarmerTrials/open-refine-export-duplicates.png)

This will prompt an automatic download to your default 'downloads' folder. We should then rename this file and store it in our project folder so we can refer to it later. So, find the file, rename it to **hh_info_duplicates** and save it into your project folder.

Now, we can remove the 14 duplicate rows:

![image](/assets/images/FarmerTrials/open-refine-delete-all-duplicates.png)

### Tip: Undo / Redo

If for any reason you make a mistake you can undo transformations from the _Undo / Redo_ menu

![image](/assets/images/FarmerTrials/open-refine-16.png){:class="size--medium-small"}

## 3. Export your data to csv

Now that our data is clean we want to import it back into our database. The easiest way to do this is to export it as a csv, which we will then import into our database. Ensure you have removed and facets or filters, then export the data:

![image](/assets/images/FarmerTrials/open-refine-17.png)

This will prompt an automatic download to your default 'downloads' folder

## 4. Import your data back into the database

Finally we can import the data back into our data.

First we will remove any existing data (This again is why it is good to have a backup).

Right-click on the table and select **Empty table(s)**

![image](/assets/images/FarmerTrials/open-refine-18.png){:class="size--medium-large"}

Now we can import the new data by clicking on _Tools_ and _Import csv file_

![image](/assets/images/FarmerTrials/open-refine-19.png)

The default settings will most likely need to be changed

![image](/assets/images/FarmerTrials/open-refine-import-back-to-heidi.png)

You might receive an error message, which will also appear at the bottom of Heidi. Read the messages to understand what the issue is and whether it is critical. The data will still be imported, but if you want to fix the issues you can reimport. Otherwise you can simply close the message.

![image](/assets/images/FarmerTrials/open-refine-20.png)

Finally you can click on the _refresh_ button to see your imported data. This time there should only be 168 rows.

![image](/assets/images/FarmerTrials/open-refine-21.png)

## 5. Remove duplicate records from plot_data

Finally, we need to resolve the issue of the records we deleted. We deleted 14 records from hh_info. We need to also **delete the corresponding records from plot_data**. We can do this within Heidi. 

Select the plot_data table. Using Heidi's filter, we can add a statement to only show records where the form_ID is in the list of deleted records. Using the list we saved earlier, create the following filter: `form_ID in (116,121,127,134,140,142,172,179,185,186,246,247,335,345)`

![image](/assets/images/Heidi/heidi-apply-filter.png)

>Note there is no semi-colon at the end of this filter. If you add a semi-colon you will get an error message and the filter will not work.

Apply this filter to only see records where the form_ID is one of the listed numbers. You should see 45 matching rows. Then, go to Edit -> Select all (or press "Ctrl + a") to select all matching rows.

![image](/assets/images/Heidi/heidi-select-all.png){:class="size--small"}

Then right-click within the table and click "Delete selected row(s)" (or press Ctrl + Del keys)

![image](/assets/images/Heidi/heidi-delete-selected.png){:class="size--small"}

## 5. Repeat the process for all other datasets

You should this process of cleaning for both _plot_data_ and _preference_data_ datasets, and try to remove as many inconsistencies as possible.

In the [next step](/case-study/farmer-plot-trials/step-4) we will link the data together using relationships.
