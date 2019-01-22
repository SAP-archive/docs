---
layout: concept
title: Expression
permalink: /concepts/expression
---

## Definition
An expression is a sentence that your bot can understand –- it's basically something that a user might say to your bot. Expressions are organized into intents and constitute the entire knowledge of your bot. The more expressions you have, the more precisely your bot can understand its users. If you've added the languages English, French, German, or Spanish to an intent, and enter a new expression for the intent in any of those languages, the platform automatically suggests additional expressions in those languages. You can then easily add the suggested expressions to the intent and quickly build up the training dataset for your bot.  

In an expression, you can annotate custom [entities](/concepts/entity) to train your bot to recognize key elements in hour sentences.

## Tips

* Put yourself in your users’ shoes; imagine what they might ask your bot.
* Keep your expressions to a reasonable length.
* An intent should contain at least 30 expressions.
* Train your bot with diversified expressions. In the following example, note how the expressions are structured differently. They try to anticipate the different ways that your user might ask for something. If all the expressions were structured the same way, for example, _I'd like pizza_, _I'd like burger …_, _I'd like salad_, your bot will have less success understanding the user.

## Example

If the intent is **order-food**, some good expressions could be:

* I'd like to order a pizza.
* Can you get pasta for me?
* How about a salad?
* A veggie burger and fries would do nicely.

## Import a CSV

The import should enable you to speed up your bot development process. 

| Key        | Required | Value  | Description                                                 |
| ---------- | -------- | ------ | ----------------------------------------------------------- |
| expression | Yes      | String | A sentence or word group                                    |
| language   | Yes      | String | The iso code representing the language                      |

<br>

Please format the CSV file as the following:
(<a href="/assets/import-examples/expressions.csv" download>Example</a>)

<br>

| expression                | language |
| ------------------------- | -------- |
| I want to travel to NYC.  | en       |
| Let's travel to New York! | en       |

<br>
There is a limit for importing expressions.
You are allowed to import 10,000 expressions at once, while not exceeding the file size limit of 1 MB.
Additionally, you cannot add the same expression multiple times to the same intent.
