---
layout: concept
title: Condition
permalink: /concepts/condition
---

A condition is a test that can be evaluated to either true or false.

You can find conditions in different sections of your skill:
- in the **<a href="/concepts/trigger">triggers</a>**
- in the **<a href="/concepts/requirement">requirements</a>**
- in each group of **<a href="/concepts/action">actions</a>**

![Recast.AI - Bot condition](//cdn.recast.ai/man/recast-ai-data-condition-ex.png)

In this example, we test:
- if the **intent** is greetings
- if the **sentiment** analyzed in the sentence is negative
- if in the **conversation memory**, the value saved for **city** is *Paris*

## Composition of a condition

A condition is made of three parts: one operator and two operands.

In the condition *if #location.raw is Paris*, the left operand is **#location.raw**, **is** is the operator and **Paris** is the right operand.

### Left operand

As a left operand, you can use any value of
<a href="https://recast.ai/docs/api-reference#request-text" target="_blank" rel="noopener noreferrer">text analyse</a>
 (intents, entities, ..) from your user input
 and any value from the
 <a href="/concepts/conversation-state">conversation state</a>
 (the last skill, memory values..).

A few rules to distinguish the left operands categories:
- operands starting by **@** will get the associated intent (for example *@greetings*)
- operands starting by **#** will get the associated entity (for example *#location*), and will test the *raw* field unless you've specified one
- operands starting by **_** will get the associated field in the [text analyze](https://recast.ai/docs/api-reference#request-text) JSON or in the conversation state

*Note*: you can write the entire path if you need, like: *#location.lat* (if you need the latitude) is the same as *nlp.entities.location.lat*. Or if you need to access the
description of the first intent detected: *nlp.intents[0].description*.

![Recast.AI - Condition Select](//cdn.recast.ai/man/recast-ai-condition-select.png)

### Operators

There's a finite list of operators you can use:
- **is** to test equality between two values
- **is-not** to test inequality between two values
- **in** to check if a value is in a list of elements
- **not-in** to check if a value is not in a list of elements
- **matches** to match a value with a regular expression
- **matches-not** to check if the value doesn't match with a regular expression
- **lower-than** to test if the value is lower than another
- **greater-than** to test if the value is greater than another
- **is-present** to test if the value is present in the **<a href="/concepts/conversation-state">conversation state</a>**
- **is-asbent** to test if the value is asbent in the **<a href="/concepts/conversation-state">conversation state</a>**

*Note*: the regex syntax follows the <a href="https://ruby-doc.org/core-2.4.1/Regexp.html" target="_blank" rel="noopener noreferrer">Ruby regex syntax</a>

*Note bis*: **greater-than** and **lower-than** only works with numerical values.

### Right operand

The right value can either be a free input or a finite list depending on what you've picked as the left operand.

For example, if you've picked *sentiment*, the right operand will be limited to what the Recast.AI API can return (in this case, from "very positive" to "very negative").
But if you've picked *_memory.my_value.my_key*, any format is supported as it's not dependent of the Recast.AI API.

You can find more details on the entities' enrichment and the other keys with a finite list of possible values
<a href="https://recast.ai/docs/api-reference#glossary" target="_blank" rel="noopener noreferrer">in the MAN</a>.

## Create complex conditions

You can create multiple layers of condition using **and** and **or**.

![Recast.AI - Bot condition](//cdn.recast.ai/man/recast-ai-skill-conditions-or-and.png)

You can see in this example two groups:
- the first group (in line) is an \`and\` condition group
- the second group (the entire block) is an \`or\` condition group
