---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Extracting data for analysis
permalink: /case-study/farmer-plot-trials/step-5
---

# Extracting data for analysis

In this step we will using [DB Forge](/tools/db-forge) to query our data and extract all of the information we need for our analysis.
We will also use the tool to build a database schema which will allow us to merge data from different datasets together

If you do not have the tool installed follow the link above for instructions.

## 1. Open dbForge Query Builder

From the start page you can access the query builder within the SQL Development tab
![image](/assets/images/FarmerTrials/dbforge-queries-1.png)

## 2. Load the database tables

In the new window that appears select your tables on the left and use drag and drop to place them in the main area on the right. If you previously created links between database tables you will also see them represented in the diagram
![image](/assets/images/FarmerTrials/dbforge-queries-2.png)

## 3. Decide the columns to populate

Using the visual builder it is very easy to select columns from multiple datasets which will automatically be merged together.

For our analysis we want to look at the striga treatment and pest data from our _plot_data_ trials, and we can merge with our background _hh_info_ data to also look at results by county.

![image](/assets/images/FarmerTrials/dbforge-queries-3.png)

> Note - if there is additional unlinked tables within the view (i.e. _preference_data_), the software will still try to merge unsuccessfully, and produce a large number of duplicate records. Therefore we should remove the _preference_data_ from our window using _right-click_->_cut_ or the _delete_ key

## 4. Confirm the join

You can see the join type from the _Joins_ tab. By default an `INNER JOIN` has been used, meaning that it will only keep records where there is information for both household and plot data. For our use case this is correct, however if you want to learn more about cases where you may want other types please refer to the relevant documentation.

![image](/assets/images/FarmerTrials/dbforge-queries-3a.png)

## 4. Execute the query

We could use dbForge to populate more advanced querying, such as use `WHERE` to filter our data or `GROUP_BY` to aggregate, however for now we will just export the data as it is (we can always filter and aggregate later within our analysis tools)

You can quickly execute the query using the _Execute_ button (F5), and you will be presented with a table of data

![image](/assets/images/FarmerTrials/dbforge-queries-4.png)

You can see that there are 619 rows of data. This means for every plot (n=619), we have also populate the hh_info data. We will not use this table however as:

> A limitation of dbForge is you can only export the first 1000 results of any query.

Whilst our data is still less than 1000 rows, it's still better to execute queries from Heidi so that we can export the full data whenever there is more than 1000 rows.

## 5. Run the query in Heidi

We can simply copy any query from dbForge into Heidi to execute.

Click on the _Text_ tab to see the full query text, and copy by highlighting and using _right-click -> copy_

![image](/assets/images/FarmerTrials/dbforge-queries-5.png)

Then open Heidi and in a _Query_ window paste

![image](/assets/images/FarmerTrials/dbforge-queries-6.png)

Excute the query by pressing the (F5) key or clicking on the _run_ button

## 6. Export your results

To export your results click on _Tools -> Export grid rows_

![image](/assets/images/FarmerTrials/dbforge-queries-7.png)

This will open a new window where you can specify output settings

![image](/assets/images/FarmerTrials/dbforge-queries-8.png){:class="size--medium-large"}

Once confirmed click _OK_ and your merged data should now be exported!

In the [final step](/case-study/farmer-plot-trials/step-6) we will briefly analyse this data using exploratory visualisation software, and produce some graphical representations.
