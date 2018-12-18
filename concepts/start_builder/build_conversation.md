---
layout: concept
title: Build your conversation
permalink: /concepts/build-your-conversation
---

## Bot Builder

To find the predefined skills that you selected when creating your bot, click the **BUILD** tab.
The gray panel on the left is your command panel. It allows you to add new skills.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/introduction/builder-workplace.png)

To explain what your skill does, which APIs it calls (if any), or even link a Git repository if your skill requires code, click the skill. A README.md opens, where you can enter this information.

## Triggers

Triggers are the conditions that need to be completed for your skill to be initiated. You can define a wide range of conditions:

* Check which intent has been detected
* Check if a specific entity has been detected
* Check if the sentiment of the user sentence is positive or negative
* Check that a **#location** entity has been detected, and that its value is, for example, *San Francisco*, *Paris*, or *Singapore*.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/recast-ai-trigger-1.png)

You can create up to two levels of conditions, and switch between an AND and an OR condition.
An AND condition is true if every element of the condition is true, whereas an OR condition is true if at least one of its elements is true.

## Requirements

A requirement is a piece of information that your bot needs to have detected and saved in its memory before continuing the conversation. This section is executed once the triggers have been executed.
You can require entities and intents. The second half of the requirement, after the *as*, is the alias of your requirement. It is under this name that you'll find it in your bot's memory.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/recast-ai-requirement-1.png)

To define how your bot asks for and then validates the requirement, click the arrow at the right end of the requirement. A settings panel opens.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/recast-ai-requirement-2.png)

If the requirement is missing (for example, **If #location is missing**), click the adjacent **+ NEW REPLIES** to define the actions that you want your bot to execute. You can send a message, call a webhook, or update the conversation, for example, by going to another skill.

![SAP Conversational AI create bot](https://cdn.cai.tools.sap/man/recast-ai-requirement-4.png)


## Actions

Actions are things that your bot does at certain points when executing a skill. They can be the following:

* Message to send back to the user
* HTTP call to your API (Webhook)
* Fallback to a human agent
* Execution of another skill
* Update the memory of the current conversation
* Change the language


