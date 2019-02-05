---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Defining relationships
permalink: /case-study/farmer-plot-trials/step-4
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

We could consider trying to join by _farmername_, however as both the prefrence_data and hh_info do not contain information about all of the same farmers (and also contain duplicates), additional steps must be taken to first remove the duplicate entries and then add an additional table that can hold a list of all farmers from both tables.

![image](/assets/images/FarmerTrials/dbforge-8.png)

This is beyond the scope of this example, however if you want more information on how this can be achieved then you can search online or feel free to contact us.

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

> In a situation where we have inconsistent records there is no standard way to resolve. You might be able to go back to the enumerator to try and determine what went wrong, or decide on a method for handling such as omitting all duplicate data or just keeping original/newer values.

For the sake of this example, let us assume that all of the newer records are correct. That gives us 2 options:

1. delete the older records, to remain only with newer
2. rename the farmers in older records, to keep both

As the data in hh_info table is also linked with the data in the plot_data table, if we wanted to delete farmers we would have to make sure we do so in both places.

To keep things simpler, and to prevent loss of any data, we will just rename the duplicate records.

### Isolate the duplicate records

We can go through the list and for each set of duplicates _flag_ the older record
![image](/assets/images/FarmerTrials/open-refine-12.png)

Once all duplicates have been flagged we can select them all using _Facet by flag_

![image](/assets/images/FarmerTrials/open-refine-14.png)

There should now be 8 records selected which we want to rename

![image](/assets/images/FarmerTrials/open-refine-15.png)

We could do this manually, or altogether by using a custom transformation:

![image](/assets/images/FarmerTrials/open-refine-15a.png){:class="size--medium"}

![image](/assets/images/FarmerTrials/open-refine-15b.png){:class="size--large"}

### Tip: Undo / Redo

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

The default settings will most likely need to be changed

![image](/assets/images/FarmerTrials/open-refine-19a.png)

You might receive an error message, which will also appear at the bottom of Heidi. Read the messages to understand what the issue is and whether it is critical. The data will still be imported, but if you want to fix the issues you can reimport. Otherwise you can simply close the message.

![image](/assets/images/FarmerTrials/open-refine-20.png)

Finally you can click on the _refresh_ button to see your imported data. This time there should only be 173 rows.

![image](/assets/images/FarmerTrials/open-refine-21.png)

## 5. Repeat the process for all other datasets

You should repeat this process for both _plot_data_ and _preference_data_ datasets, and try to remove as many inconsistencies as possible.

In the [next step](/case-study/farmer-plot-trials/step-5) we will be using queries to merge data from all of these datasets together for use in our analysis.
