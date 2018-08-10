---
layout: concept
title: Action
permalink: /concepts/action
---

Actions are, well, actions your bot executes at specific time in the skill execution.

## Action categories

An action can either be:

- a **message** to send back to the user
- a **Webhook call** to request your API
- a **redirection** to execute another skill
- a memory **edition** for the current conversation
- a switch to another **language**

![Recast.AI - Action](//cdn.recast.ai/man/recast-ai-actions-type.png)

## Message actions

Various format exists, so you can build an awesome UX for your bots.

If your bot is connected to a channel through Bot Connector, these messages type will be adapted to the channel constraint and transformed, so the look and feel will probably change compared as what you see on the Recast.AI platform.

You can find more informations about this [messages format](https://recast.ai/docs/concepts/builder_messages).

![Recast.AI - Messages types](//cdn.recast.ai/man/recast-ai-type-of-messages.png)

You can dynamically inject the content gathered from the conversation in the bot replies by using the double braces syntax.

Ex: your bot asks for the user's name as a requirement. Once the requirement completed, you will have the name in the memory of the bot.

You can then create a text message (or every other messages actually) filled with: "Hello {{memory.username.raw}}". Then {{memory.username.raw}} will be replaced with the actual username.

You can find more informations about this [variable system](https://recast.ai/docs/concepts/builder_messages).


## Webhook actions

At many points in your conversation, you most likely want to retrieve business information or connect to an external system to perform actions. You can do this through webhooks. A webhook is a simple HTTP call to your backend. To configure your HTTP call, click **CALL WEBHOOK** in the Bot Builder.

![Recast.AI - Webhook](//cdn.recast.ai/man/webhook/header.png)

When your url is called, a default body is sent with the complete state of conversation. You can send back messages you want to send to the user, as well as an updated conversation state. Everything you need to know about webhooks is described in [this section](https://recast.ai/docs/concepts/code-and-webhook).

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

First the memory is reset, then the new values are set, and finally the specified keys are unset. Leanr more about memory edition [in this dedicated section](https://recast.ai/docs/concepts/memory-management).

![Recast.AI - Memory action](//cdn.recast.ai/man/recast-ai-memory-action.png)

> Note that you can also use **variables**, as in the *messages* actions described above.
