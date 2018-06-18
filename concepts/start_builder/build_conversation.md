---
layout: concept
title: Build your conversation
permalink: /concepts/build-your-conversation
---

Click on the **BUILD** tab to find the predefined skills you have selected when creating your bot.
The grey section on the left is your command pannel. It allows you to create new blocks, called **SKILLS**.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-what-skill-1.png)

Hover one of your skills, and click on it to edit it.
You arrive on a new page, the page of your skill, containing a README. The README.md is the ideal place to explain what your skill does, what APIs it calls (if any), and even linking a git repository if your skill requires code.


## Triggers


Triggers are the conditions that need to be completed for your skill to be "triggered". You can define a wide range of conditions:
* check what intent has been detected
* check if a specific entity has been detected
* check if the sentiment of the user sentence is positive or negative
* check that a **#location** entity has been detected, and that its value is "San Francisco", "Paris", or "Singapore".

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-trigger-1.png)

You can create up to two levels of conditions, and switch between an **AND** and an **OR** condition.
An **AND** condition means that every element of the condition has to be true for the condition to be true, whereas an **OR** condition is true if at least one of its element is.

## Requirements

A requirement is an information your bot needs to have detected and saved in his memory before continuing the conversation. This section is executed once the triggers have been executed.
You can require two things: **entities** and **intents**. The second half of the requirement, after the *as*, is the alias of your requirement. It is under this name that you will find it in the memory of your bot.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-1.png)

You can click on the arrow at the right end of the requirement to open an settings panel. Here, you can define how your bot asks for and then validates the requirement.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-2.png)

Click on the first "SEND REPLIES", corresponding to "if my requirement is complete". There, you can define the actions your bot has to execute once the requirement is met. You can add messages, call webhooks or go to another skill.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-4.png)

When there is no usable information in the user input, you can setup specific messages by creating actions with "SEND REPLIES".

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-3.png)

Just below this section, you have the **Validator** section. You can define custom conditions, exactly like those defined in your trigger, to validate that the requirement is valid.
So if you have a **#location** in your requirement, but want to continue the conversation only if the location is "Paris", you can set a condition.
If the condition is not valid, the location won't be added in the memory of the bot, and instead the action defined for this validator will be performed. Again, you can define the actions for a validator by clicking on the "SEND REPLIES"
next to the conditions.

You can define multiple validations, each with its own replies.

## Actions

Actions allow your bot to actually do things when you need to. An action can either be:
* A message to send back to the user
* An HTTP call to your API
* The execution of another skill
* Reset the memory of the current conversation

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-action-1.png)

