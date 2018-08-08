---
layout: concept
title: Requirement
permalink: /concepts/requirements
---

Requirements are either **intents** or **entities** your skill needs to retrieve before executing actions.
They are pieces of information that are important in the conversation and that your bot can use, like the name of the user or a location.

Once a requirement is completed, the associated value is stored in the memory of the bot for the entire conversation.

![Recast.AI - Requirements](//cdn.recast.ai/man/recast-ai-memory-box.png)

## **Composition of a requirement**

A requirement is made of:

- the data to retrieve, an **entity** or an **intent**
- the key that will be used to store the data retrieved in the bot memory
- optional actions to execute to retrieve the information
- optional actions to execute when the information is retrieved and the requirement completed
- optional conditions to validate the data provided by the user, with associated actions to execute if the validation fails

![Recast.AI - Requirement content](//cdn.recast.ai/man/recast-ai-requirement-2.png)

### Action at requirement completion

Those actions are executed when the requirement is completed.
The skill's execution then continues as far as it can.
It can chain with other requirements, or with
 **<a href="/concepts/action">actions</a>**

![Recast.AI - Action complete](//cdn.recast.ai/man/recast-ai-action-complete.png)

### Actions to retrieve information

Those actions are executed when the requirement is not yet completed. It's the perfect place to define messages to ask the information you need to the user.
For example, with the username as a requirement, the action would be a message asking the user for his name.

![Recast.AI - Action missing](//cdn.recast.ai/man/recast-ai-action-missing.png)

### Validators

You can define validators in a requirement to validate that the user input matches your needs.
These validators are made of **<a href="/concepts/condition">conditions</a>** and actions to execute in case of a validation error.

The validation fails when the condition is **true**. In such case, the retrieved data will not be stored in memory, and thus the requirement will not be completed.

For example, if we want to get a city from the user, we can create a requirement that retrieves a location entity, and add a validator to check that this location is really a city and does not refer to a country for example, and tell the user about this limitation.

You could write it this way :
```
if #location.type is-not locality
  send_message('Can you please give me a city ?')
```

![Recast.AI - Validators action](//cdn.recast.ai/man/bot-builder/validators.png)

## **Group of requirements**

Like conditions, requirements can be grouped together with **OR** and **AND**.

![Recast.AI - Requirement](//cdn.recast.ai/man/recast-ai-requirement-1.png)
