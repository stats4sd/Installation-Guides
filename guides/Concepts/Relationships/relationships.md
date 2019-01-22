---
layout: default
section: Concepts
title: Database Relationships
permalink: /concepts/relationships
---

# Database Relationships

## Linking Tables

Having a set of data tables is great, but the real power of SQL comes when you start linking these tables together.

Before you can link two tables in SQL, you must have a good understanding of what the data in those tables actually represents. See the best practice guide on [building your tables](/resources/building-tables){:target="_blank"} for help with this.

## Types of relationship
You may have heard of different types of relationship. These are common across all types of relational database, including Microsoft Access, MySQL, PostgreSQL and Oracle DB.

### One to One

The simplest type of relationship: A record in Table 1 is linked to at most 1 record in Table 2. For example, in your farmer research network, you might have a number of farmers, represented in a table of farmers. Some farmers have an account on your website, but each farmer can only have 1 account. So, Your `farmers` table has a one-to-one relationship with your `web_accounts` table.

To create this in the database, you link 1 field in your secondary table to the primary key in your main table. In the example here, the web_accounts table has a `farmer_id` field, which corresponds to the `id` field in the farmers table. The `farmer_id` becomes a "foreign key".

**Which is your secondary table?**
If one of your tables depends on another it can be called the secondary. In our example, it doesn't make sense to have a record in `web_accounts` if there isn't a corresponding record in `farmers`. (As a farmer must exist to have a user account on your site!). So, your `web_accounts` table is the secondary table in this example.

![image](/assets/images/relationships/1-1.jpg)

### Many to One

A record in Table 1 is linked to any number of records in Table 2. For example, a farmer can have many plots. 1 record in the `farmers` table can be linked to many records in the `plots` table, so these tables have a many-to-one relationship.

In the database, this is represented in a similar way to one-to-one relationships - by adding a "foreign key" field to your secondary table. In this case, the 'secondary' table is always the 'many' table. So, in the example here, the tables are linked via the `farmer_id` field in the `plots` table. That field tells you which farmer each plot belongs to. One farmer can have many plots, (e.g. Farmer 3 has 2 plots), but a single plot can only belong to one farmer.

![image](/assets/images/relationships/many-1.jpg)

### Many to Many:

A record in Table 1 is linked to any number of records in Table 2, **and** a record in Table 2 is linked to any number of records in Table 1.

This relationship is impossible to represent with just the 2 tables required, but is still quite a common occurance in real life. For example, you might work with NGOs, who all work in multiple regions within a country. Each NGO works in 1 or more regions, and each region has 1 or more NGOs active within it. This means you have a many-to-many relationship between your `ngos` table and your `counties` table. 

So, how do we model this relationship? We cannot just add a `county_id`  as a foreign key to the `ngos` table, as there could be any number of regions linked to one NGO. We also cannot just add an `ngo_id` as a foriegn key to the `counties` table, because there can be any number of NGOs linked to one region. 

Instead, we create a link table - a table that sits in between the 2 main tables, which acts as the "secondary" table for both. This link table has the 2 columns `ngo_id` and `county_id`. Each record represents 1 line that can be drawn between the 2 main tables.

![image](/assets/images/relationships/many-many.png)

This link table is often called a 'pivot' table by database managers, but "link table" is also understood.

### Link table features
Just like any other table, this table requires a primary key - a way of uniquely identifying each row. Remember that this can be a combination of fields, and it's good practice to use the combination of both fields in your link table. In our example above, this means your primary key is both `ngo_id` and `county_id`. This means that, for example, you will ensure you never have 2 records linking the same ngo and county together, as that would be redundant and might result in strange results when you query your database.

One other thing to consider is naming of your link tables. Many people suggest using the convention of concatenating the 2 tables you are linking, in alphabetical order - e.g.: counties_ngos. This can work well, but I personally prefer to make it even more clear which tables are "link" tables. So, I start each link table name with `_link`. That way, when my tables are sorted alphabetically, all the link tables appear together at the top of the list.