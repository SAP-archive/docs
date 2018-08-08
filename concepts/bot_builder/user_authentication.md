---
layout: concept
title: User Authentication
permalink: /concepts/user-authentication
---

This User Authenitcation concept is only available if you are using the Bot Builder API directly (not through the Bot Connector), through your dedicated webchat in your website for example.

It let you use possible tokens, cookie session, user ID that you may have because you know that your user is logged in your website, and you want to use these kind of information to authenticate webhook call in Recast.AI

* You can add these uniq user identifiers by setting specific keys in the memory field when you initiate a new conversation during the first request made to the /dialog endpoint.
* This field will contain a user-defined value (for example, authentication token or a user id of the client side database)

-> Check the [API documentation](https://recast.ai/docs/api-reference/#dialog-endpoints) of this API endpoint to undersant how to format your API request

Example of a `POST /dialog` request body with the `memory` field (let say that the token for my user is `myAwesomeUniqueToken`):
~~~ json
{
  "message": {
    "content":"Hello Recast",
    "type":"text"
  },
  "conversation_id": "CONVERSATION_ID",
  "memory": {
    "identifierToken": "myAwesomeUniqueToken"
  }
}
~~~


* This way, during the entire conversation, you can access this memory field and use it in webhook actions, in headers or in authentication fields for example:

![Recast.AI - webhook with variables](//cdn.recast.ai/man/bot-builder/headers-with-id.png)
