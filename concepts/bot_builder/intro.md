---
layout: concept
title: Introduction
permalink: /concepts/builder-intro
---

This is a introduction regarding how Bot Builder interacts with other services of the platform.

## Introduction

The Bot Builder process is split in three disctincts parts:
- Get the user’s input through a messaging channel
- Understand user’s input using Natural Language Processing
- Manage the conversation and the context

1) Getting the user input can be done by the Bot Connector, meaning the Bot Connector when receiving a message is going to disptach the message to your Bot Builder. By default every single messages received by Bot Connector is sent to the https://api.recast.ai/build/v1/dialog which is the endpoint of your Bot Builder.

2) Once the Bot Builder receives an input, it posts the message on our NLP API to extract structured information from this sentence

3) The last step consists of using the JSON that it got back from the NLP API to manage the conversation using Skills and conditions.


## Bot Builder with Bot Connector

If you're using the Bot Builder with Bot Connector, as stated above all incoming messages are sent byt the Bot Connector to the 

An action can either be:

- a **message** to send back to the user
- an **HTTP call** to your API
- the **redirection** and execution of another skill
- an **edition** of the memory of the bot for the current conversation
- a switch to another **language**

![Recast.AI - Action](//cdn.recast.ai/man/recast-ai-actions-type.png)

## Bot Builder without Bot Connector


## Message actions
For message actions, all rich messaging formats are supported.

![Recast.AI - Messages types](//cdn.recast.ai/man/recast-ai-type-of-messages.png)

Formatting:
You can inject variables in your messages by using the double braces syntax.
For example, *{{nlp.source}}* will be replaced by the input sentence.

Here is a list of the more useful ones:

* **{{nlp.source}}**: raw user input.
* **{{nlp.entities.location[0]}}**: first entity detected of the type \`location\`. You can replace \`location\` by any entity name you want.
* **{{#location.raw}}**: same as above, get the first entity location detected, and get its raw field.
* **{{nlp.sentiment}}**: <a href="https://recast.ai/docs/api-reference#sentence-sentiments" target="_blank" rel="noopener noreferrer">sentiment</a> of the sentence
* **{{nlp.act}}**: <a href="https://recast.ai/docs/api-reference#sentence-acts" target="_blank" rel="noopener noreferrer">act</a> of the sentence
* **{{nlp.type}}**: <a href="https://recast.ai/docs/api-reference#sentence-types" target="_blank" rel="noopener noreferrer">type</a> of the sentence
* **{{nlp.intents[0].slug}}**: slug of the first intent detected
* **{{memory.person.raw}}**: a value stored in the memory of the bot. Here *person* is the alias of a requirement
* **{{skill}}**: slug of the current skill
* **{{skill_occurrences}}**: number of consecutive occurrences of the current skill

![Recast.AI - Action](//cdn.recast.ai/man/recast-ai-action-2.png)

## HTTP actions

For webhooks (HTTP actions) you can either provide a full url, or simply a route that is added to your bot's base url (updatable in your bot settings).

![Recast.AI - Webhook action](//cdn.recast.ai/man/recast-ai-webhook-action.png)

When your url is called, you receive the complete state of conversation:

~~~ json
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
    "skill": "small-talk",
    "skill_occurences": 1,
    "participant_data": {}
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

You can send back messages you want to send to the user, as well as an updated conversation state.

## Go to actions

You can use Goto action to indicate which skill should be executed next.

![Recast.AI - Goto action](//cdn.recast.ai/man/recast-ai-goto-action.png)

You have two options:

- **Start the skill** will bypass the triggers of the skill and directly try to resolve the requirements and the actions.
- **Wait for the user input** serves as an indicator, the next user input will try to enter this skill in priority, but triggers will be applied.

Note: you can use a **variable** instead of the name of the skill, as in the *messages* actions described above.

## Language actions

This action allows you to modify the language of the conversation.

![Recast.AI - Language action](//cdn.recast.ai/man/recast-ai-language-action.png)

It can be especially useful when your user asks "Can you speak Spanish?" for example.

## Memory edition actions

Theses actions allow you to do three different things:

* Reset the entire memory of the conversation
* Set values in the memory
* Unset a key in the memory

First the memory is reset, then the new values are set, and finally the specified keys are unset.

![Recast.AI - Memory action](//cdn.recast.ai/man/recast-ai-memory-action.png)

> Note that you can also use **variables**, as in the *messages* actions described above.
