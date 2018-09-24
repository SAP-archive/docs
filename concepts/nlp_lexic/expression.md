---
layout: concept
title: Expression
permalink: /concepts/expression
---

## Definition
An expression is a sentence that your bot can understand –- it's basically something that a user might say to your bot. Expressions are organized into intents and constitute the entire knowledge of your bot. The more expressions you have, the more precisely your bot can understand its users. Whenever you add an expression to an intent, Recast.AI automatically suggests additional expressions that you can then quickly and easily also add to the intent. 

In an expression, you can annotate entities to make them appear in the Recast.AI response and use them in your code.

## Tips

* Put yourself in your users’ shoes; imagine what they might ask your bot.
* Keep your expressions to a reasonable length.
* An intent should contain at least 30 expressions.
* Train your bot with diversified expressions. In the following example, note how the expressions are structured differently. They try to anticipate the different ways that your user might ask for something. If all the expressions were structured the same way, for example, _I'd like …_, _I want …_, _I fancy …_, your bot will have less success understanding the user.

## Example

If the intent is **order-food**, some good expressions could be:

* I'd like to order a pizza.
* Can you get pasta for me?
* How about a salad?
* A veggie burger and fries would do nicely.


