---
layout: post
category: Python
title: Sending email programmatically with Python
---

Below is the code:

<!-- more -->
```python
# you need install the smtplib package
import smtplib

# sender email address
fromaddr = 'your-email-address'

# recipient email address
toaddrs = 'target-email-address'

# email content
msg = "\r\n".join([
    "From: "+fromaddr,
    "To: "+toaddrs,
    "Subject: Email from Python!",
    "",
    "Hi there!"
])

# your gmail account
username = 'your-email-address'
password = 'your-email-password'

server = smtplib.SMTP('smtp.gmail.com', 587)
server.ehlo()
server.starttls()
server.login(username, password)
server.sendmail(fromaddr, toaddrs, msg)

# do not forget to quit the server
server.quit()

```
