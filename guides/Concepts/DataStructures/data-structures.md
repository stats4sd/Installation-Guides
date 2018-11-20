---
layout: default
section: Concepts
title: Working With Data Structures
permalink: /concepts/data-structures
---

# Working with Data Structures

## MySQL Tables
In MySQL, your data are stored in a collection of tables. You can imagine a  table like a single sheet in Excel, or a single .csv file. The variables in your data are the columns, often called 'fields', and the entries are the rows - often called 'records'. So a table of farmers with 4 fields (columns) and 3 records (rows) could look like this:

| id | farmer_name | age | community_id |
|----|-------------|-----|--------------|
|  1 | Mary        |  23 |            2 |
|  2 | Joan        |  35 |            3 |
|  3 | Jake        |  28 |            3 |

The easiest way to create tables is to use an SQL client - you can learn more about clients in the tools section of this pack. You can also create tables directly with an SQL command `CREATE TABLE tblname ( columns )`. For example, to create the above table, you might use:

```
CREATE TABLE farmers (
    `id` INT(11) UNSIGNED PRIMARY_KEY,
    `farmer_name` VARCHAR(100),
    `age` INT(11) UNSIGNED,
    `community_ID` INT(11) UNSIGNED,    
    );
```

This defines the names and data types for each of the 4 fields. It also defines `id` as the Primary key for the table.

## Primary Keys
Every table must have a primary key. This is a unique way to identify every record within the table. It is usually a single field, (such as an `id` field), but can sometimes be a combination of different fields. For example, if you have data from different weather stations, you might choose to use the station_id combined with the timestamp of the record to be the primary key, as the combination of these fields will always be unique. 

If you don't have a primary key in your data before entering it into a database, you can create one by creating an INT field with the `AUTO_INREMENT` property. This field will automatically populate with incrementing numbers - the first record will contain "1", the next "2", etc. 

>**IMPORTANT:** Never use something like "Name" as the primary key. Even if you think you're unlikely to find 2 people with identical names in your project, it's still possible. Instead, you should create another variable to be your primary key, such as an `id` integer field. 

## MySQL Data Types
Each field has a data type. This is defined when you create the table, and all the data entered into that field must conform to the same data type. 

There are a lot of different data types, but only a few that you will use regularly. These are: 

### Text Data:
 - **VARCHAR(_size_)**: Holds a variable length string. When you define a VARCHAR, you must define a maximum size for the string. For example, a field defined as `VARCHAR(3)` can have 0 - 3 characters. This wouldn't be suitable for a field containing people's names, but would be suitable for storing ISO country codes. The maximum length you can specify for a varchar is 255 characters.
 - **TEXT**: This is for longer strings of text, for example a free-form text response in a survey, or a short interview transcript. It holds a maximum of 65,535 characters. Unlike VARCHAR, you do not need to specify a maxmimum length, so you define a field simply as `TEXT`. 
 - **LONGTEXT**: For when 65 thousand characters simply will not do. `LONGTEXT` fields can store up to 4,294,967,295 characters. (This is the equivalent of a 4GB text file!)

### Numeric Data
- **INT(_size_)**: Holds an integer. This data type has 2 useful properties:
    + size: This is not the maximum number that can be stored, but the maximum number of digits that will be displayed. The default is INT(10), and there's not much reason to use a different size.
    + signed / unsigned: You can define whether the field accepts negative integers. By defining a field as UNSIGNED, any value will be assumed positive. Unsigned INT fields have a range of 0 to 4294967295. Signed INT fields have a ranger of -2147483648 to 2147483647. The default is "signed". You can define an unsigned field using `INT(10) UNSIGNED`.
- **BIGINT(_size_)**: For when you need bigger integers. This acts the same as INT (including the properties of size and signed/unsigned), but accepts numbers in the range -9223372036854775808 to 9223372036854775807 for SIGNED and 0 to 18446744073709551615 for UNSIGNED fields.
- **DECIMAL(_precision_,_scale_)**: Holds a decimal number. When defining a decimal, you must give 2 properties: 
    + Precision: The number of significant digits that are stored for values;
    + Scale: the number of digits that can be stored after the decimal point.
 So, for example, `DECIMAL(5,2)` defines a field that can store numbers from -999.99 to 999.99. `DECIMAL(7,5)` would have a range of -99.99999 to 99.99999.

### Date / Time Data:
- **DATE()**: A date, in the ISO format (YYYY-MM-DD). For example: 2018-11-20.
- **DATETIME()**: A date and time combination, in the ISO format YYYY-MM-DD HH:MI:SS. For example: 2018-11-20 17:05:23.
- **TIMESTAMP()**: A timestamp is a date/time field stored as the number of seconds since the Unix epoch (1st January 1970). Timestamps are often used for "date created" and "date updated" fields, and accept inputs in the same formats as DATE() and DATETIME() fields. 

There are other data types, but the ones listed here will probably be enough for most situations. For a full list of data types available in MySQL, see the [w3schools.com reference page](https://www.w3schools.com/sql/sql_datatypes.asp).


### Data Types Q&A

**Why not define all varchar fields as `VARCHAR(255)`?**
This is certainly an option. There is no real performance hit to using VARCHAR(255) instead of VARCHAR(20). The main reason to use a shorter length is as a validation check on your data. If you have a table of countries and are storing the 3-character ISO code for each country, you might want to use `VARCHAR(3)`. This way, any strings that are too long will be flagged before entering the database.

**Why use VARCHAR at all? Why not just use TEXT or LONGTEXT?**
An important technical reason is Indexing: You cannot use a TEXT field as part of an index, but you can for a VARCHAR. This means that a TEXT field cannot be your primary key, or a foreign key, or have any sort of constraint (e.g. unique) applied.

The other reason is more philosophical. A big reason to use SQL is so you can pre-define your data structures. Making all your strings `TEXT` means you probably haven't thought about what sort of data you are expecting to go into those fields. Think about whether you are likely to need more than 255 characters - I suspect you won't for most of your data. When you do need to store longer strings, still think whether you need TEXT or LONGTEXT. `LONGTEXT` can store up to 4GB of text in a single cell - imagine a 4GB text file, then decide whether you actually need that! If you don't need it, don't use it, as you will avoid potential performance problems later on.






