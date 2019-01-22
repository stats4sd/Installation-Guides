---
layout: default
section: Resources
title: MySQL For Excel Tips
permalink: /resources/mysql-for-excel-tips
---

# MySQL For Excel Tips

When using the MySQL for Excel tool it is likely that the schema automatically generated will not be a perfect fit for your data.

Below are a few tips to ensure your data integrity is preserved:

_If you are not familiar with using the MySQL for Excel plugin it is recommended you first view the_  
_[Farmer Plot Trials](/case-study/farmer-plot-trials) case study_

## 1. Check Every Column

It is important that you systematically go through every column to check the data type that has been allocated correctly.

![image](/assets/images/Resources/mysql-for-excel-1.png)

## 2. Consider VarChar() lengths

Anywhere excel detects text it will format as VarChar, and use the cell with longest text in the column as the length limit. Often you should change this to allow for text that receive larger entries in the future.

![image](/assets/images/Resources/mysql-for-excel-2.png){:class="size--medium-small"}

This will be fine if our IDs stay consistent, although if they could change we might want to add a few more characters. Columns like names will definitely need to have reasonable maximum length.

For more information on best practice for VarChar lengths see <a href="/concepts/data-structures" target="_blank">Working with Data Structures</a>

![image](/assets/images/Resources/mysql-for-excel-3.png){:class="size--medium-small"}

Any column where we will be entering text, such as a comment or feedback form should probably be formatted as **Text** Data Type instead of VarChar

## 3. Ensure Boolean columns correct

Excel may try to convert columns to boolean and may omit others. You should therefore check carefully

![image](/assets/images/Resources/mysql-for-excel-4.png){:class="size--medium-small"}

Excel will try to convert the 'yes'/'no' responses to True/False (0/1) boolean values, however as the 'yes' is not capitilised ('Yes'), it will instead import incorrectly as false (0). It would be better to keep this column as text, or clean before import.

![image](/assets/images/Resources/mysql-for-excel-5.png){:class="size--medium-small"}

This column should be in Boolean format, as the 0 corresponds to a false value and 1 to a true value in our data (there are no other numbers present). We can therefore set the Data Type as **Boolean**
