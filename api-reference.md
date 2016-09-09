---
layout: page
title: WhatsMate API Reference
subtitle: WhatsApp Messaging, Telegram Messaging, Translation
---

<br/>

# Table of Contents
* [API Host](#api-host)
* [Common HTTP Header](#common-http-header)
* [Authentication](#authentication)
* [WhatsApp Gateway Endpoints](#whatsapp-gateway-endpoints)
* [Telegram Gateway Endpoints](#telegram-gateway-endpoints)
* [Translation Endpoints](#translation-endpoints)


<br/>
<hr/>
## API Host

All REST API endpoints are hosted on `http://api.whatsmate.net/`.

If you prefer `https`, you can use `https://whatsmate-api.appspot.com/`.


<br/>
<hr/>
## Common HTTP header

You should include the following HTTP header in your call to any one of the endpoints:

- `Content-Type: application/json`


<br/>
<hr/>
## Authentication

You authenticate yourself against the API server with your `Client ID` and `Client Secret`. You obtain them by subscribing to a premium plan.

They are carried in these HTTP headers: `X-WM-CLIENT-ID` and `X-WM-CLIENT-SECRET`.

Example:
<pre>
X-WM-CLIENT-ID: elsa@example.com
X-WM-CLIENT-SECRET: 53654f8ee3684a37201e3c90a071dbd7
</pre>



<br/>
<hr/>
# WhatsApp Gateway Endpoints

### 1. Check the status of the WhatsApp gateway
* Endpoint: `GET /v1/gateway/status`
* Parameters required: None
* Response: Json containing the following property:
  * `status`: Either "up" or "down"  <br><br>


### 2. Send a WhatsApp message
* Endpoint: `POST /v1/whatsapp/queue/message`
* Parameters required in JSON payload:
  * `number`: String. The destination phone number including the country code. No "+" sign is needed.
  * `message`: String. The text message that you want to send.
* Response:
  * `{ 'status': 'queued'}`



<br/>
<hr/>
# Telegram Gateway Endpoints

### 1. Check the status of the Telegram gateway
* Endpoint: `GET /v1/telegram/status/{instance_number}`
* Parameter required in URL: 
  * `instance_number`: Possible value: 0
* Response: Json containing the following properties:
  * `status`: Either "up" or "down"
  * `instance`: The instance number of the gateway
* Example request: `GET /v1/telegram/status/0`  <br><br>


### 2. Send a Telegram message to a single recipient
* Endpoint: `POST /v1/telegram/single/message/{instance_number}`
* Parameter required in URL: 
  * `instance_number`: Possible value: 0
* Parameters required in JSON payload:
  * `number`: String. The phone number of the recipient including the country code. No "+" sign is needed.
  * `message`: String. The text message that you want to send.
* Response: Json containing these properties:
  * `success`: Possible values: `true` / `false`
  * `status`: String. Text explaining what happened.


<br/>
<hr/>
# Translation Endpoints

### 1. Translate text
* Endpoint: `POST /v1/translation/translate`
* Parameters required in JSON payload:
  * `fromLang`: String. The code representing the language of the supplied text.
  * `toLang`: String. The code representing the language you want the text to be translated to.
  * `text`: String. The piece of text you want to be translated.
* List of lanugage codes: See the next endpoint.
* Response: String. The translated text.  <br><br>


### 2. List all the possible language codes
* Endpoint: `GET /v1/translation/supported-codes`
* Parameters required: None
* Response: JSON showing all the possible language codes.

