---
layout: concept
title: Create your chatbot
permalink: /concepts/create-builder-bot
---

Here is the first steps to understand the core concepts of the Recast.AI platform. You will be able to build a chatbot that can manage an entire conversation with a user.

A Recast.AI chatbot is composed of two main *hearts* : **Skills** and **Training Dataset**.

A **Skill** is a block of conversation that has a clear purpose and that your bot can execute to achieve a goal. You will need to configure these skills to build the scope of your bot.

A **Training Dataset** is composed of lot of sentences organised in [intents](https://recastai.github.io/docs/concepts/intent) that represent what user can say to your chatbot to train it to understand their needs and be able to trigger the right piece of conversation, reply correctly and have a smooth conversation.

*Ready?* Click on the **+ New Bot** button, on the top right and start create your first chatbot.

## Select predefined skills

You can choose one or several predefined skills you want to use as a starting point. Select the **Greetings** one to start.
You are free to modify them if you don't like them as such, or even delete them once you're ready to make your own.

If you want to fork them later on, they are available here: [https://recast.ai/scaffolder/starter-skills](https://recast.ai/scaffolder/starter-skills)

![Recast.AI create bot](https://cdn.recast.ai/man/introduction/predefined-skills.png)

## Create your bot

Finish your bot creation by:
* Choosing a name and a description
* Setting the default language (it is possible to add more languages later)

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-create-builder-3-body.png)

## Discover your first intents and skills

If you have selected **greetings** skill, in the **TRAIN** tab you can find two intents: **greetings** and **goodbye**.

An intent is a *box* of sentences that all carry the same meaning, even though they can be very different to one another. When a user sends some text to your bot, our algorithm predicts to which intents it’s close enough and decides what the intention of the message is.

For example:

*Are you a bot?*

*You reply so fast, I’m sure you must be some kind of robot.*

*Am I speaking to a human or not?*

are all different, but they all ask the same question that we can can sum up as: Are you a bot? Well, that would make a great intent! If your bot is able to recognize this question, you can prepare a smart reaction, like “I’m a robot and I’m proud of it “.

In the **BUILD** tab, you can find two skills: **greetings** and **fallback**


