---
layout: concept
title: Code and webhook
permalink: /concepts/code-and-webhook
---


If you want to extend Bot Builder with custom code, you can call your API with webhook actions.

![Recast.AI - Webhook url](//cdn.recast.ai/man/recast-ai-webhook-view.png)

You must provide a full url or route (starting with a '/') to be called by Bot Builder, allowing you to run code or API calls.

If you provide a route, it will be added to your bot's base url (configurable in your bot's settings).

![Recast.AI - Bot url settings](//cdn.recast.ai/man/recast-ai-settings-bot-url.png)

## What your code will receive

You will receive a POST HTTP request on this route, with all the conversation state.

Then you can perform any calculation, database checks or external API calls and send back data to Bot Builder.
The body format is the following:

~~~ javascript
{
  "conversation": {
    "id": "A_CONVERSATION_ID",
    "language": "en",
    "memory": {
      "person": {
        "fullname": "Francois",
        "raw": "Francois",
        "confidence": 0.95
      }
    },
    "skill_stack": ["get-weather"],
    "skill": "small-talk",
    "skill_occurences": 1
  },
  "nlp": {
    "source": "hi",
    "intents": [
      {
        "slug": "greetings",
        "confidence": 0.99
      }
    ],
    "sentiment": "vpositive",
    "entities": {},
    "act": "assert",
    "type": null,
    "version": "2.10.1",
    "processing_language": "en",
    "language": "en",
    "uuid": "96597974-3ee1-4743-8a5d-341b67effb9a"
    "status": 200,
    "timestamp": "2017-10-25T21:36:02.071243+00:00",
  }
}
~~~

Warning: as of right now, you can't authenticate the requests coming from Recast.AI, so your API has to be opened.

## How to format your reply?

Send back a formatted message, Bot Builder will forward it to the user.
Of course all messages format from Bot Connector are supported.
