---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Defining relationships
permalink: /case-study/farmer-plot-trials/step-3
---

# Defining relationships

In this step we will build links between the tables. This will enable us to extract information from both at the same time during querying, and will also help ensure we don't have missing data in our database in the future. We will be using the software <a href="/tools/db-forge" target="_blank">dbForge</a>

## 1. Open dbForge

Whilst it is possible to do everything using Heidi, dbForge offers a nice visual tool to create and view relationships. Anything created here will exist as part of our database, and so still be available to Heidi.

![image](/assets/images/FarmerTrials/dbforge-1.png)

## 2. Create a new database diagram

The diagram will allow us to visually represent links between tables. You can access it from the _Database Design_ tab

![image](/assets/images/FarmerTrials/dbforge-2.png)

## 3. Add your tables to the diagram

Tables are listed in the left-hand side. You can add these to the diagram using drag and drop, or by _right-click_ -> _send to_ -> _database diagram_

![image](/assets/images/FarmerTrials/dbforge-3.png)

If your tables show up too small you can resize them and arrange the diagram to better-fit the available space.

![image](/assets/images/FarmerTrials/dbforge-4.png)

## 4. Add your first database relationship

We will define a relationship from _plot_data_ to _hh_info_. We know that these tables are linked by the _form_ID_ field, and that for each household there can be multiple plots. Therefore we will be using a _many-to-one_ relationship, starting from plot_data (many) and ending with hh_info (one)

Select the _New Relation_ tool, then draw a line from the form_ID field in plot_data to the form_ID field in hh_info.

![image](/assets/images/FarmerTrials/dbforge-5.png)

A popup window will appear to confirm the relationship information. If everything was done correctly you should see the following information.

![image](/assets/images/FarmerTrials/dbforge-6.png){:class="size--medium"}

Click _Apply Changes_ to finish creating the link. You will see the link represented by a solid line on the diagram.

![image](/assets/images/FarmerTrials/dbforge-7.png){:class="size--medium"}

## 5. Creating more relationships

We have not yet linked our preference data to the other tables. This is more challenging as there is not a natural one-to-one or many-to-one relationship between the data in this table and any others.

We could consider trying to join by _farmername_. However, as both the prefrence_data and hh_info do not contain information about all of the same farmers (and also contain duplicates), additional steps must be taken to first remove the duplicate entries and then add an additional table that can hold a list of all farmers from both tables.

![image](/assets/images/FarmerTrials/dbforge-8.png)

This is beyond the scope of this example, however if you want more information on how this can be achieved then you can search online or feel free to contact us.

In the [next step](/case-study/farmer-plot-trials/step-4), we will do some data cleaning and create a set of 'processed' data tables that we can use for querying.
