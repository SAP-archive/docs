---
layout: concept
title: Expression
permalink: /concepts/expression
---

## Definition
An expression is a **sentence** your bot can understand: basically your **users’ inputs**. Expressions are organized in intents and constitute the entire knowledge of your bot. The more expressions you have, the more precisely your bot will be able to understand its users. In an expression, you can annotate entities to make them appear in the Recast.AI response and use them in your code.

## Tips
* Take the time to put yourself in your users’ shoes, imagine what they might ask to your bot
* Try to keep the length of your expressions reasonable
* An intent should contain at least 30 expressions
* Train your bot with diversified expressions

## Example

Intent: \`want-food\`

**DOS**
* I want to eat cheese
* I really like apples, can I eat some?
* Can you give me some pastas?
* I'm hungry, I would love pizza

**DON'TS**
* I want to eat cheese
* I want to eat pizza
* I would like to eat a pizza
* I like cheese
