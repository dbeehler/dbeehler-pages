---
title: Web Investigation Lab
layout: default
parent: Cyber Defenders
---

# Web Investigation Lab

# Key Takeaways

- On March 15th, 2024 starting at 12:01 PM, an attak was observed on `bookworldstore.com`
- The attacks were sent through the search function. Specifically, the `search.php` file was susepetible to SQLi (SQL Injection).
- The attacker utilized guest permissions to enumerate and infiltrate customer database records
- The attacker was able to bruteforce the admin login and upload files to the site

# Table of Contents

- [Web Investigation Lab](#web-investigation-lab)
- [Key Takeaways](#key-takeaways)
- [Table of Contents](#table-of-contents)
- [Case Summary](#case-summary)
- [Analysts](#analysts)
- [Initial Access](#initial-access)
- [Exploitation](#exploitation)
- [Exfiltration](#exfiltration)
- [Discovery](#discovery)
- [Privelege Escalation](#privelege-escalation)
- [Persistence](#persistence)


# Case Summary

An attack was successfully executed on the Bookworld Store website.

Starting with manual recon and moving into automated means, the attacker was able to elevate to admin priveleges and exfiltrate customer data. The attacker was able to then upload a PHP reverse shell to the webserver through he admin permissions.

It should be assumed that this webserver was/is fully compromised.

# Analysts

[Dusty Beehler](https://www.linkedin.com/in/dbeehler/)

# Initial Access

Initial Access was gained as a *guest* user of the website `bookworldstore.com`. From here, the attacker (Source IP of **111.224.250.131**) manually enumerated endpoints by exploring the website as evident from the network traffic.
![Manual Network Traffic](https://dbeehler.github.io/dbeehler-pages/images/cyber-defenders/web-investigation-lab/manual_exploring.png)

# Exploitation

Upon discovering the search feature, the attacker attempted to execute SQL commands through the `search.php` script. Between 12:03:52 and 12:09:57, the user submitted 126 requests attempting to perform different SQL actions. After 12:07:34, the User Agent of the HTTP requests switched to `sqlmap/1.8.3#stable` indicating that the attacker was using the popular SQLi bruteforcing application SQLMap.

# Exfiltration

The SQLmap application was able to enumerate all database information. The attacker started with printing the table names and then moving on to examine the `admin` table.

The attacker was able to return the admin users's username and password which was used later in the attack. Additionally, they were able to print information from the customer database including addresses, emails, names, and phone numbers.

# Discovery

In addition to using SQLmap, the attacker utilized gobuster. Gobuster is a command line tool to brute force directories on a web server. Using this, they were able to locate the `/admin`.

# Privelege Escalation

Using the admin permissions gained before, the attacker logged in as the admin user at 12:17:35.

# Persistence

After logging into an admin account, the user was able to locate the upload functionality. They successfully uploaded a file, `NVri2vhp.php` at 12:24:18. 

Due to the nature of the lab, this is the last recorded activity available.