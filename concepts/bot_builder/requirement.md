---
layout: concept
title: Requirement
permalink: /concepts/requirements
---

Requirements are either intents or entities that your skill needs to retrieve before executing 
[actions](https://cai.tools.sap/docs/concepts/action).
Requirements are pieces of information that are important in the conversation and that your bot can use, for example, the user's name or a location.

Once a requirement is completed, the associated value is stored in the bot's memory for the entire conversation.

![SAP Conversational AI - Requirements](//cdn.cai.tools.sap/man/recast-ai-memory-box.png)

## **Composition of a requirement**

A requirement is made up of the following:

- Data to retrieve, that is, an entity or intent
- Key to store the retrieved data in the bot's memory
- Optional actions to execute to retrieve the information
- Optional actions to execute when the information is retrieved and the requirement is completed
- Optional conditions to validate the data provided by the user, with associated actions to execute if the validation fails

![SAP Conversational AI - Requirement content](//cdn.cai.tools.sap/man/recast-ai-requirement-2.png)

### Optional actions to execute to retrieve the information

These actions are executed when the requirement is not yet completed. It's the perfect place to define messages to ask the user for the information you need.
For example, with the username as a requirement, the action would be a message asking the user for their name.

![SAP Conversational AI - Action missing](//cdn.cai.tools.sap/man/recast-ai-action-missing.png)

### Optional actions to execute when the information is retrieved and the requirement is completed

These actions are executed when the requirement is completed.
The skill's execution then continues as far as it can.
It can chain with other requirements or with actions.

![SAP Conversational AI - Action complete](//cdn.cai.tools.sap/man/recast-ai-action-complete.png)


### Optional conditions to validate the data provided by the user, with associated actions to execute if the validation fails

You can define validators in a requirement to validate that the user input matches your needs.
These validators are made up of **[conditions](https://cai.tools.sap/docs/concepts/condition)** and actions to execute in case of a validation error.

The validation fails if the condition is **true**. In such cases, the retrieved data is not stored in memory and the requirement is not completed. For example, if we want to get a city from the user, we can create a requirement that retrieves a location entity. We can add a validator to check that this location really is a city (and doesn't, for example, refer to a country). If the location isn't a city, we can then ask the user for a city. You could write it like this:
```
if #location.type is-not locality
  send_message('Can you please give me a city ?')
```

![SAP Conversational AI - Validators action](//cdn.cai.tools.sap/man/bot-builder/validators.png)

## **Grouping requirements together**

Like conditions, you can group requirements together with **OR** and **AND**.

![SAP Conversational AI - Requirement](//cdn.cai.tools.sap/man/recast-ai-requirement-1.png)
