---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Creating a database
permalink: /case-study/farmer-plot-trials/step-1
---

# Creating a database

In this first step we will create a database that will be used to store the trial, household and plot information.

We will be creating a new [MySQL](/tools/mysql) database using [Heidi](/tools/heidi). If you are unsure of either of these software packages follow the links to the tools page.

## 1. Open Heidi

## 2. Login as the root user

Or any other login with permissions to create database

## 3. Create a new database and profile for the demo

![image](/assets/images/Heidi/heidi-create-db.png){:class="size--medium-large"}

You will be prompted to set the database name and _collation_ type.

We are using the name _farmer-trials-demo_ and collation _utf8_unicode_ci_

![image](/assets/images/Heidi/heidi-create-farmer-trials-db.png){:class="size--medium-large"}

## 4. Assign permission for your regular user on the database

If you do not have additional users you can skip this step, although it is strongly recommended that you do.

Open the user management tool

![image](/assets/images/Heidi/heidi-user-management-button.png){:class="size--medium-large"}

Select the user you wish to give access to this database, and then select **Add object**

![image](/assets/images/Heidi/heidi-user-permissions.png){:class="size--medium"}

Finally select the database and permissions you wish to grant.

![image](/assets/images/Heidi/heidi-add-object.png){:class="size--medium"}

For this tutorial we will add all permissions on our new farmer-trials-demo database.

![image](/assets/images/Heidi/heidi-grant-priviledges.png){:class="size--medium"}

Remember to click **save** when you are finished!

## 5. Disconnect from the root user

You can click the disconnect icon ![image](/assets/images/Heidi/heidi-icon-disconnect.png){:class="size--xx-small"}

## 6. Log back in as your regular user account

This is the account we just gave permissions to

## 7. Check you can access the database

If this worked successfully you should see the database listed in the column on the left

![image](/assets/images/Heidi/farmer-trials-db-list.png){:class="size--medium-small"}
