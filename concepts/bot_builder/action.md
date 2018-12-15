---
layout: concept
title: Actions
permalink: /concepts/action
---

An action is something that your bot executes at a specific point when executing a [skill](https://recast.ai/docs/concepts/what-skill). To add actions to a skill, open the skill on the **Build** tab and then open the **Actions** subtab and click **ADD NEW MESSAGE GROUP**.

## Action categories

An action can be one of the following:

- Send message to the user
- Call webhook
- Fallback (that is, redirect the conversation to a human agent)
- Go to another skill
- Edit the bot's memory for the current conversation
- Change language

![Recast.AI - Action](//cdn.recast.ai/man/actions-type.png)

A message group can contain one or more actions. You can easily reorder actions within a message group by drag and drop; look for the **Move** icon below the action on the left. You can also reorder entire message groups by drag and drop; look for the **Move the group** icon at the bottom of the message group on the left.

## Send message to the user

Various formats exist, enabling you to build an awesome user experience for your bots.

If your bot is connected to a channel through the Bot Connector, the message type is adapted to the channel constraint and transformed, so the look and feel will probably change compared with what you see on the SAP Conversational AI platform. For more information, see [Message format](https://recast.ai/docs/concepts/builder_messages).

![Recast.AI - Messages types](//cdn.recast.ai/man/recast-ai-type-of-messages.png)

You can dynamically inject the content gathered from the conversation in the bot replies by using double brace syntax. For example, if your bot asks for the user's name as a requirement, the name is added to the bot's memory once the requirement is completed. You can then create a text message (or any other message actually) filled with "Hello {{memory.username.raw}}", where {{memory.username.raw}} is replaced with the actual username. For more information, see [Variable system](https://recast.ai/docs/concepts/builder_messages).

## Call webhook

At many points in your conversation, you most likely want to retrieve business information or connect to an external system to perform actions. You can do this through webhooks. A webhook is a simple HTTP call to your backend. To configure your HTTP call, click **CALL WEBHOOK** in the Bot Builder.

![Recast.AI - Webhook](//cdn.recast.ai/man/webhook/header.png)

When your URL is called, a default body is sent with the complete conversation state. You can send back messages you want to send to the user, as well as an updated conversation state. For more information, see [Custom code and webhooks](https://recast.ai/docs/concepts/code-and-webhook).

## Fallback

This action lets you redirect the conversation to a human agent. First, you need to connect the fallback channel where you want SAP Conversational AI to redirect the message. You can do this on the **Connect** tab by selecting a fallback channel and following the instructions. After connecting the fallback channel, remember to activate it by checking the input.

![Recast.AI - Fallback action](https://cdn.recast.ai/man/fallback-channel.png)

In a skill, you can configure a fallback action by selecting your fallback channel and the group to which you want to redirect the conversation. (Usually, your support center is organized into different groups.) When the fallback action is triggered, the bot doesn't reply, but instead sends the conversation history to your support channel, where a human agent writes a reply that is redirected to the user. When the human agent closes the ticket or conversation in your support center, the bot is able to talk to the user again.

![Recast.AI - Fallback action](https://cdn.recast.ai/man/fallback-action.png)

## Go to another skill

You can use this action to indicate which skill should be executed next.

![Recast.AI - Goto action](//cdn.recast.ai/man/recast-ai-goto-action.png)

You have two options:

- **Start the skill** will bypass the triggers of the skill and directly try to resolve the requirements and actions.
- **Wait for the user input** serves as an indicator. The next user input will try to enter this skill in priority, but triggers will be applied.

> Note: You can use a variable instead of the name of the skill, as described above in *Send message to the user*.

## Edit the bot's memory for the current conversation

This action lets you do three different things:

* Reset the entire memory of the conversation
* Set values in the memory
* Unset a key in the memory

First the memory is reset, then the new values are set, and finally the specified keys are unset. For more information, see [Memory management](https://recast.ai/docs/concepts/memory-management).

![Recast.AI - Memory action](//cdn.recast.ai/man/recast-ai-memory-action.png)

> Note: You can also use variables, as described above in *Send message to the user*.

## Change language

This action lets you change the language of the conversation. It can be especially useful if your user asks, for example, "Can you speak Spanish?".

![Recast.AI - Language action](//cdn.recast.ai/man/recast-ai-language-action.png)

