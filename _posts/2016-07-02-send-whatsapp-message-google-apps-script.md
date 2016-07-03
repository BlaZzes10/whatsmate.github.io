---
layout: post
title: How to send WhatsApp Messages from Google Apps Script
subtitle: Using the WhatsMate WA Gateway REST API
published: true
---

This article shows you how to send a WhatsApp message from a Google Apps Script.

Before the recipient can receive your WhatsApp message, she will need to register with the WhatsMate WA Gateway. Instructions are available on the [official site](http://www.whatsmate.net/whatsapp-gateway.html). *Unregistered users will NEVER receive messages from the Gateway.*


To send a WhatsApp message from a Google Apps Script, do this:

1. Copy the following source code to your Apps Script project.  <script src="https://gist.github.com/whatsmate/96637d1c46e1a199756f18413e739f7b.js"></script>
2. Specify your target recipient on line 2. Remember to include the country code.
3. Specify your message on line 3.
4. Run the function `main()` to send your message.


The trial account allows you to send up to 100 messages per day. [Upgrade to the Premium Account](http://www.whatsmate.net/premium-account.html) to send unlimited number of messages.

