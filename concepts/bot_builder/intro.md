---
layout: concept
title: Introduction
permalink: /concepts/builder-intro
---

This is an introduction to how the Bot Builder interacts with the other services of the platform.

The Bot Builder process is split into three distinct parts, each of which is described in more detail below.

1) Get the user’s input through a messaging channel.

2) Understand the user’s input using Natural Language Processing (NLP).

3) Manage the conversation and context.

### Get the user's input
This can be done by the Bot Connector, meaning that when the Bot Connector receives a message, it dispatches the message to your Bot Builder. You can also collect the user's input by your own way and send it to the Bot Builder API directly.

### Understand the user's input
Once the Bot Builder receives an input, it posts the message to our NLP API to extract structured information from this sentence.

### Manage the conversation and context
This consists of using the JSON, which was returned from the NLP API, to manage the conversation using skills and conditions.

<img class='custom' src='https://cdn.cai.tools.sap/man/bot-builder/bot-builder-01.png'>

## Bot Builder with Bot Connector

If you're using the Bot Builder with Bot Connector, all incoming messages are sent by the Bot Connector to the Bot Builder API (as described above). By default, every single message received by the Bot Connector is sent to the https://api.recast.ai/build/v1/dialog endpoint, which is the endpoint of your Bot Builder.

The Bot Builder then replies to the Bot Connector with messages formatted as described in [Structured messages](https://cai.tools.sap/docs/concepts/structured-messages).

<img class='custom' src='https://cdn.cai.tools.sap/man/bot-builder/bc-bb-01.png'>

## Bot Builder without Bot Connector

You need to retrieve the user input by your own way, for example, through a channel that you've implemented. You then directly request the Bot Builder API and follow the [Dialog endpoints](https://cai.tools.sap/docs/api-reference/#dialog-endpoints) documentation in the API Reference to create a new conversation.




