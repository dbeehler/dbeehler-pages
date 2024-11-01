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
- [Takeaways](#takeaways)


# Case Summary

# Analysts

[Dusty Beehler](https://www.linkedin.com/in/dbeehler/)

# Initial Access

Initial Access was gained as a *guest* user of the website `bookworldstore.com`. From here, the attacker (Source IP of **111.224.250.131**) manually enumerated endpoints by exploring the website as evident from the network traffic.
[![Manual Network Traffic](/images/cyber-defenders/web-investigation-lab/manual_exploring.png)](https://dbeehler.github.io/dbeehler-pages/images/cyber-defenders/web-investigation-lab/manual_exploring.png)

# Exploitation

Upon discovering the search feature, the attacker attempted to execute SQL commands through the `search.php` script. Between 12:03:52 and 12:09:57, the user submitted 126 requests attempting to perform different SQL actions. After 12:07:34, the User Agent of the HTTP requests switched to `sqlmap/1.8.3#stable` indicating that the attacker was using the popular SQLi bruteforcing application SQLMap.

# Exfiltration


# Discovery



# Privelege Escalation



# Persistence


# Takeaways