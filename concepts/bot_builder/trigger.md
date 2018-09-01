---
layout: concept
title: Trigger
permalink: /concepts/trigger
---

Triggers are
**<a href="/docs/concepts/condition">conditions</a>**
 that determine whether the bot should execute the current skill or not.

If the trigger conditions of the skill are validated, the bot will execute it over other skills.

If a skill has **no triggers**, it will never be executed by a user input, but only if it is at the end of a redirection by another skill.

![Recast.AI - Linked skills](//cdn.recast.ai/man/recast-ai-linked-skills.png)

Skills with the **fallback** type do not have triggers, as they are automatically triggered when no other skill is, or when an error occurs (like if two skills are triggered at the same time).

> Note that you can have only one fallback skill per builder.

![Recast.AI - Trigger](//cdn.recast.ai/man/recast-ai-trigger-1.png)
