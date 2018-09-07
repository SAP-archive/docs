---
layout: concept
title: Build your conversation
permalink: /concepts/build-your-conversation
---

To find the predefined skills that you selected when creating your bot, click the **BUILD** tab.
The gray panel on the left is your command panel. It allows you to add new skills.

![Recast.AI create bot](https://cdn.recast.ai/man/introduction/builder-workplace.png)

To explain what your skill does, which APIs it calls (if any), or even link a Git repository if your skill requires code, click the skill. A README.md opens, where you can enter this information.

## Triggers

Triggers are the conditions that need to be completed for your skill to be initiated. You can define a wide range of conditions:

* Check which intent has been detected
* Check if a specific entity has been detected
* Check if the sentiment of the user sentence is positive or negative
* Check that a **#location** entity has been detected, and that its value is, for example, *San Francisco*, *Paris*, or *Singapore*.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-trigger-1.png)

You can create up to two levels of conditions, and switch between an AND and an OR condition.
An AND condition is true if every element of the condition is true, whereas an OR condition is true if at least one of its elements is true.

## Requirements

A requirement is a piece of information that your bot needs to have detected and saved in its memory before continuing the conversation. This section is executed once the triggers have been executed.
You can require entities and intents. The second half of the requirement, after the *as*, is the alias of your requirement. It is under this name that you'll find it in your bot's memory.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-1.png)

To define how your bot asks for and then validates the requirement, click the arrow at the right end of the requirement. A settings panel opens.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-2.png)

If the requirement is complete (for example, **If #location is complete**), click the adjacent **+ NEW REPLIES** to define the actions that you want your bot to execute. You can send a message, call a webhook, or update the conversation, for example, by going to another skill.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-4.png)

Likewise, if there is no usable information in the user input, define the actions that you want your bot to execute.

![Recast.AI create bot](https://cdn.recast.ai/man/recast-ai-requirement-3.png)

Below this, you have the option to add validators. This lets you define custom conditions, exactly like those defined on the **Triggers** tab, to validate that the requirement is valid. For example, if you have a #location in your requirement, but want to continue the conversation only if the location is Paris, you can set a condition. If the condition is not valid, the location isn't added to your bot's memory, and instead the action defined for this validator is performed. You define the actions for the validator by clicking the adjacent **+ NEW REPLIES**. You can define multiple validators, each with its own replies.

## Actions

Actions are things that your bot does at certain points when executing a skill. They can be the following:

* Message to send back to the user
* HTTP call to your API
* Fallback to a human agent
* Execution of another skill
* Reset the memory of the current conversation
* Change the language


