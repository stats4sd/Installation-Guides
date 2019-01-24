---
layout: default
section: Concepts
title: Best Practice When Building Tables
permalink: /concepts/building-tables
---

# Creating Good Tables

Tables are the core of your SQL database.

## What tables do I need?

Whilst it might be possible to store all of the information for your project in just one or two tables, like a giant excel spreadsheet, this is often not good to do. As your database grows it gets harder to understand and extract the data you need, and it also makes it more difficult to integrate data from other sources, or make changes to data structures.

For example, imagine you are conducting a simple variety trial. You want to collect data about each farm and data about each plot used in the trial, including the variety used, the total yield, and the farmer's observations. This means you have 2 tables for your collected data:

- one for the farm data you collect;
- one for the 'plot' data you collect.

There are also other pieces of data you will use to help make sense of this collected data. You would have a list of farmers in your network - some of whom will be involved in the trial. So it makes sense to have a seperate `farmers` table. This table can keep information related to farmers who both are, and are not directly involved with this trial. You will also have a list of crop varieties used in the trial. So you will need a `varieties` table to hold any data you have about each variety.

**Why seperate data like this?**:

- It's more flexible. Your `farmers` table can be used for this trial, but it can also be used for any other experiments run in the network.

- It's more efficient. For example, any properties of a specific variety can be stored in one place - your `varieties` table, instead of being repeated in your plot data for every plot where that variety is grown. This makes your data much easier to keep up-to-date, or make changes such as fixing a spelling mistake or to add a local translation to the varieties - you just need update one place instead of many.

## Main tables

How can you identify when your data needs a single table, and when it should be in multiple tables? An important rule to remember is:

> A table should only contain data about one type of entity. Each record is a specific instance of that entity, and each column should be a property of that entity.

### Find the Nouns

The challenge here is to identify the groups that make sense for your data. You may want to consider this as finding the important _nouns_ in your project. In agricultural trials, these might include:

- Communities
- Farms
- Farmers (not always the same as farms!)
- Plots
- Varieties
- Soil types
- Management practices
- Farmer typologies
- Observations or survey responses (e.g. the data you collect at different points in the study.) - these might be split into multiple tables. For example, you might need one table for a survey conducted mid-season, and one table for another survey conducted at the end of the season.

Following this practice, you might quickly have a lot more tables in your database!

## Lookup Tables

If you have already designed your data collection forms, you will probably have a number of 'select' or multiple-choice questions. If you've been thorough at finding your nouns, you may already have tables for each of these select questions. For example, "select the variety used" can pull straight from your `varieties` table.

But there may be lists for select questions you want to define that aren't pulled directly from an existing table. For example, you might have a set of categories for the 'prevalence of a disease' in a plot. The question in your data collection form would ask the user to choose from these categories. It's a good idea to store these categories within your database, instead of just within your data collection form. This has a few important benefits:

- If the data is coded you can automatically export data either with their codes or their corresponding labels.
- A complete set of lookup tables can act as a data dictionary, allowing others looking at your data to better undertand the meaning of your main tables.
- It allows you to re-use common lists in multiple studies. This is the same concept as reusing your `farmers` table for multiple studies within the same network.

### Structure and Naming

It's a good idea to name your lookup tables it's clear what they are. It is also good to name things in a systematic way so that all _lookup_ tables can easily be distinguished and grouped together. Common ways to do this are using naming prefixes, such as `_lkp_tablename`. We start with an '\_' so that also all lookup tables are grouped at the start alphabetically, alongside other tables where you might only be storing metadata.

A lookup table is usually very simple. At a minimum it has:

- `id`: The primary key. This typically corresponds to the 'value' of the choice in a data collection form.
- `label`: This is typically what you would want to show in a report, or to the enumerators in a data collection form.

Most lookup tables just need these columns. If you are working in multiple languages, you might have 1 label column per language. For example: `label_english`, `label_swahili`, `label_spanish`.

### Lookup table, or not?

Sometimes, you might find that you start adding more columns to a lookup table, and eventaully find that it's no longer jut a lookup table. This is perfectly fine, and often happens when your data structures start to evolve over the course of multiple projects. When this happens, you may choose to rename the table (to remove the "\_lkp\_" prefix), or you may choose to create an entirely new table and link it (1-1) to the existing lookup table. If you choose to rename the existing table, be very careful about checking your existing saved queries! Your table relationships will remain intact, but any queries or saved mysql views that reference the table will need updating.

## Link Tables

The other type of table you may have is a 'link' table (sometimes called a 'pivot' table by database managers). This table represents a many-many relationship between 2 of your main tables. For more information, see the guide on [Database Relationships](/concepts/relationships){:target="\_blank"}
