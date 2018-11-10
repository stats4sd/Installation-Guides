---
layout: default
section: Tools
title: Google Cloud SQL
permalink: /tools/cloud-sql
---

# Google Cloud SQL

## Connect to an instance from a local client

You can connect to a Google Cloud SQL instance with the same tools as you use to connect to a MySQL or PostgreSQL database anywhere else.

By default, Google prevents access from unauthorised IP addresses. This is very good practice for security reasons, as without your intervention is is very hard for people to access your potentially sensitive data.

_write something about creating a database for production and secure datasets vs testing databases or not secure data_

### Setup the Cloud SQL to accept incoming connections:

1. Authorise IP addresses to access the server:

- Click add network. In the Network field enter 0.0.0.0/0. Click done.

When this network is enabled, you will see a warning, saying this is potentially insecure.

![](/Users/Shared/Dropbox (SSD)/Screenshots/Screenshot 2018-10-26 10.55.24.png)

2. Set SSL:

- Even with testing databases, it is good practice to enable some security. In the SSL connections section, click to "Allow only SSL connections". This ensures that only users with a valid SSL certificate and client key can access the server.

3. Create a client certificate for your computer.

- Each client requires a seperate SSL certificate and key. You should never share keys between users or computers. If you want to log in from 2 different computers, you should create a certificate and key for each computer seperately.
- Click "Create a client certificate".
- Enter a recognisable name (e.g. the name or description of the computer, like dave-laptop or emily-desktop).
- You will see a popup screen with 3 sections. Download the following files:
- client-key.pem
- client-cert.pem
- server-ca.pem.

Put these files somewhere safe.

I recommend creating a folder called ".ssl" in your main user folder. On most platforms, folders with names starting with a dot are hidden by default, so it's a good way of keeping these types of config files out of the way.

Depending on your client, you may need all 3 of these files to connect via SSL. Some clients require only 2.

---

## **Note**: If you are connecting with Heidi, you do not need the server-ca.pem file. Heidi does ask for all 3 files when creating an SSL connection, but if you add the Server certificate it gives an error. This is a known bug in Heidi, but you can still connect fine by only using the client key and client certificate files.
