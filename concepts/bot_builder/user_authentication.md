---
layout: concept
title: User authentication
permalink: /concepts/user-authentication
---

This user authentication concept is only available if you're using the Bot Builder API directly (not through the Bot Connector), for example, through your dedicated webchat in your website. If you know that your user is logged in to your website, this authentication concept lets you use a token, cookie session, or user ID to authenticate the webhook call in SAP Conversational AI.

You can add these unique user identifiers by setting specific keys in the memory field when you initiate a new conversation during the first request made to the /dialog endpoint.
This field will contain a user-defined value (for example, an authentication token or user ID of the client-side database).

To understand how to format your API request, see [/Dialog (Text)](https://cai.tools.sap/docs/api-reference/#dialog-endpoints) in the API Reference.

Below is an example of a `POST /dialog` request body with `memory` field. In this example, the token for the user is `myAwesomeUniqueToken`):
~~~ json
{
  "message": {
    "content":"Hello SAP Conversational AI",
    "type":"text"
  },
  "conversation_id": "CONVERSATION_ID",
  "memory": {
    "identifierToken": "myAwesomeUniqueToken"
  }
}
~~~

![SAP Conversational AI - webhook with variables](https://cdn.cai.tools.sap/man/bot-builder/headers-with-id.png)
