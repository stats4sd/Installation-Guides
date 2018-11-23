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
We will create a new project and import our original excel data.

![image](/assets/images/FarmerTrials/open-refine-1.png){:class="size--large"}

Click **Next**

You will see a preview of your data. By default it will try to incorrectly merge all of the sheets into a single file, and so we must make sure only to select a single sheet. We will first use the `hh_info` sheet

![image](/assets/images/FarmerTrials/open-refine-2.png)

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

In this situation there is no standard way to resolve such issues, you may look through each record to see if they are duplicates, try to identify which record is correct by some other means, or possibly omitting all duplicate data from your analysis.

For this example we know that a duplicate record indicates the enumerator making a correction, and as such we should only keep the newest records.

We can **click on each farmer name** in our list, and use the star tool to **mark the rows we intend to delete** using the _flag_ icon.

![image](/assets/images/FarmerTrials/open-refine-12.png)

When you arrive at the farmername _'other'_ we will mark both of these rows to delete as the data is not valid.

![image](/assets/images/FarmerTrials/open-refine-13.png)

Finally we can delete the marked rows by creating a new facet on our flag column,

![image](/assets/images/FarmerTrials/open-refine-14.png)

then select the records that match as 'true' for our flag, and finally use the _edit rows_ and _Remove all matching rows_ to delete the records.

![image](/assets/images/FarmerTrials/open-refine-15.png)

This should reduce our total from 182 rows to 175.

If for any reason you make a mistake you can undo transformations from the _Undo / Redo_ menu

![image](/assets/images/FarmerTrials/open-refine-16.png){:class="size--medium-small"}

## 3. Export your data to csv

Now that our data is clean we want to import it back into our database. The easiest way to do this is to export it as a csv, which we will then import into our database.

![image](/assets/images/FarmerTrials/open-refine-17.png)

This will prompt an automatic download to your default 'downloads' folder

## 4. Import your data back into the database

Finally we can import the data back into our data.

First we will remove any existing data (This again is why it is good to have a backup).

Right-click on the table and select **Empty table(s)**

![image](/assets/images/FarmerTrials/open-refine-18.png){:class="size--medium-large"}

Now we can import the new data by clicking on _Tools_ and _Import csv file_

![image](/assets/images/FarmerTrials/open-refine-19.png)

You might receive an error message. If it says the data was imported then this is most likely fine and you can simply close it

![image](/assets/images/FarmerTrials/open-refine-20.png)

Finally you can click on the _refresh_ button to see your imported data. This time there should only be 175 rows.

![image](/assets/images/FarmerTrials/open-refine-21.png)

## 5. Repeat the process for all other datasets

You should repeat this process for both _plot_data_ and _preference_data_ datasets, and try to remove as many inconsistencies as possible.

In the [next step](/case-study/farmer-plot-trials/step-4) we will be using queries to merge data from all of these datasets together for use in our analysis.
