---
layout: concept
title: Skill
permalink: /concepts/what-skill
---

A skill is a block of conversation that has a clear purpose and that your bot can execute to achieve a goal. It can be as simple as the ability to greet someone, but it can also be more complex,
like giving movie suggestions based on information provided by the user.

![Recast.AI - Workspace](//cdn.recast.ai/man/recast-ai-what-skill-1.png)

A skill is not limited to one exchange with the user. In the movie suggestion example, the skill runs through multiple exchanges. It starts by asking the type of the movie, then
the year of publication and then the language of the film before making the actual suggestion.

You can link your skills together to create more complex conversations.

## Skill types

You can create three different types of skills:
* **business**, for skills closely linked to the core purpose of your bot
* **floating**, for small talk skills, topics not closely related to the core purpose of your bot
* **fallback**, the skill triggered if no other skill is.

![Recast.AI - Skill types](//cdn.recast.ai/man/recast-ai-what-skill-2.png)

You can have **only one fallback** skill per builder.

There is no execution difference between **business** and **floating** skills. The only thing that changes is the color to help you navigate through your flow.

## Skill composition

A skill is made of three distinct parts:
- **<a href="/concepts/trigger">triggers</a>**: conditions determining if the skill should or shouldn't be activated
- **<a href="/concepts/requirement">requirements</a>**: determining the information the bot needs to retrieve from the user, and how to retrieve it
- **<a href="/concepts/action">actions</a>**: performed by the bot when all requirements are complete (for example, send a message)

![Recast.AI - Skill logic](//cdn.recast.ai/man/recast-ai-skill-logic.png)
