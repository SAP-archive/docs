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

1) Getting the user input can be done by the Bot Connector, meaning the Bot Connector when receiving a message is going to disptach the message to your Bot Builder. Users input can also be collected by your own way and then sent to the Bot Builder API directly.

2) Once the Bot Builder receives an input, it posts the message on our NLP API to extract structured information from this sentence

3) The last step consists of using the JSON that it got back from the NLP API to manage the conversation using Skills and conditions.

<img class='custom' src='https://cdn.recast.ai/man/bot-builder/bot-builder-01.png'>

## Bot Builder with Bot Connector

If you're using the Bot Builder with Bot Connector, as stated above all incoming messages are sent by the Bot Connector to the Bot Builder API. By default every single messages received by Bot Connector is sent to the https://api.recast.ai/build/v1/dialog endpoint, which is the endpoint of your Bot Builder.

Bot Builder is then replying to Bot Connector with messages formatted in [this way](https://recast.ai/docs/concepts/structured-messages).

<img class='custom' src='https://cdn.recast.ai/man/bot-builder/bc-bb-01.png'>

## Bot Builder without Bot Connector

You will need to retrieve users's input by your own way, maybe through a channel you have implemented. You will directly request the Bot Builder API, and will follow [this documentation](https://recast.ai/docs/api-reference/#dialog-endpoints) to create new conversation.


