---
layout: concept
title: Create your chatbot
permalink: /concepts/create-builder-bot
---

## Introduction

Here are the first steps to understand the core concepts of the SAP Conversational AI platform. You'll then be able to build a chatbot that can manage an entire conversation with a user.

An SAP Conversational AI chatbot is composed of two main elements: **Skills** and a **training dataset**.

A **skill** is a block of conversation that has a clear purpose and that your bot can execute to achieve a goal. You need to configure these skills to build the scope of your bot.

A **training dataset** is composed of many sentences organized into [intents](https://sapconversationalai.github.io/docs/concepts/intent) that represent what users say to your chatbot. The training dataset is used to train the bot to understand the user's needs and to trigger the right piece of conversation, reply correctly, and have a smooth conversation.

Ready? Click **+ New Bot** at the top right of the page and let's create your first chatbot.

## Select predefined skills for your bot

You can choose one or several predefined skills to use as a starting point. Let's select **Greetings**.
You're free to modify them if you don't like them as such, or even delete them once you're ready to make your own.

If you want to fork the skills later on, they're available here: [https://cdn.cai.tools.sap/scaffolder/starter-skills](https://cdn.cai.tools.sap/scaffolder/starter-skills)

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/introduction/predefined-skills.png)

## Create your bot

1) Enter a name and (optional) a description.

2) (Optional) Add up to six topics to your bot (for example, *Customer Support*, *HR*, *Payments*, etc.). By categorizing your bot in this way, we can suggest more appropriate training data to improve it later.

3) Set the default language. You can add more languages later. 

4) Specify whether your bot is public or private.

5) Click **CREATE A BOT**.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/introduction/create-bot.png)

## Discover your first intents and skills

### Train

If you selected the skill **Greetings**, you'll see two intents on the **Train** tab: **greetings** and **goodbye**.

An intent is a collection of sentences that all have the same meaning, even though they can be very different to one another. When a user sends a message to your bot, our algorithm predicts to which intents it’s close enough and decides what the intention of the message is. Here are three examples of sentences with the same meaning:

*Are you a bot?*

*You reply so fast, I’m sure you must be some kind of robot.*

*Am I speaking to a human or not?*

They're all different, but they all ask the same question that we can can sum up as *Are you a bot?* Well, that would make a great intent! If your bot is able to recognize this question, you can prepare a smart reaction, like *I’m a robot and I’m proud of it*.

### Build

On the **Build** tab, you'll find two skills: **greetings** and **fallback**. Click **greetings**. You'll see that a skill has four parts:

**README.md**: Where you explain the purpose of the skill.

**Triggers**: Where you define why this skill should be activated after a user message.

**Requirements**: What information this skill has to collect, and what questions need to be asked to fulfill the requirements.

**Actions**: What to do once the requirements are fulfilled.


If you navigate through the tabs, you’ll see that this skill is structured as follows:

It is triggered if the intention **greetings** or **goodbye** is matched.
It has no requirements because it does not need to collect additional information. This means that it will execute actions directly after a trigger.
It has two possible actions. If the intention matched is **greetings**, it sends a random welcoming message chosen from a list. If the intention is **goodbye**, it does the same thing, but picks the message from a different list.

