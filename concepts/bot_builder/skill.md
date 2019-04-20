---
layout: concept
title: Skill
permalink: /concepts/what-skill
---

A skill is a block of conversation that has a clear purpose and that your bot can execute to achieve a goal. It can be as simple as the ability to greet someone, but it can also be more complex,
like giving movie suggestions based on information provided by the user.

You can add a skill to your bot on the **Build** tab by clicking **+ Create skill** in the gray command panel on the left. You can add as many skills to your bot as you wish.

![SAP Conversational AI - Workspace](//cdn.cai.tools.sap/man/recast-ai-what-skill-1.png)

A skill is not limited to one exchange with the user. In the movie suggestion example, the skill runs through multiple exchanges. It starts by asking the type of the movie, then
the year the movie was released, and then the language of the movie before making the actual suggestion.

You can link your skills together to create more complex conversations.

## Skill types

You can create three different types of skills:

* **Business**: Skills that are closely linked to the core purpose of your bot.
* **Floating**: Smalltalk skills, that is, topics that are not closely related to the core purpose of your bot.
* **Fallback**: Skill that is triggered if no other skill is triggered. Your bot can only have one fallback skill. So when you add a skill to your bot, the skill type **Fallback** is offered only if your bot doesn't already have a fallback skill.

There is no execution difference between business skills and floating skills. The only thing that changes is the color to help you navigate through your flow.

![SAP Conversational AI - Skill types](//cdn.cai.tools.sap/man/recast-ai-what-skill-2.png)

## Skill composition

A skill is made up of three distinct parts:

- **<a href="/docs/concepts/trigger">Triggers</a>**: Triggers are conditions that determine whether the skill should be activated.
- **<a href="/docs/concepts/requirements">Requirements</a>**: Requirements determine the information that the bot needs to retrieve from the user, and how to retrieve it.
- **<a href="/docs/concepts/action">Actions</a>**: Actions are performed by the bot (for example, send a message) when all requirements are complete.

![SAP Conversational AI - Skill logic](//cdn.cai.tools.sap/man/recast-ai-skill-logic.png)

## Skill groups

If you have a lot of skills, you can organize them in skill groups for better housekeeping:

1. In the gray command panel on the right, switch to **List view**.

2. In the gray command panel on the left, click **Create skill group**.

3. Enter a name for the skill group and click **CREATE GROUP**.

4. Select the skills you want to add to the skill group, click the **Select group to move** dropdown, select the group, and click the checkmark. The skill group is then activated.
