## Your conversation memory

Each conversation with a uniq user got a memory object from the beginning to the end of the conversation. This memory is persistant during the entire conversation, can be updated at any moment and clear when you want.

This memory is an empty object when a new conversation starts (unless you want to start a new conversation with pre filled keys), is stored in your <a href="/concepts/conversation-state">conversation state</a>, returned in the <a href="/concepts/code-and-webhook#body-configuration">default body</a> of webhook and returned after the Bot Builder API call.

Your memory object could look like this:
~~~ json
"memory": {
  "person": {
    "fullname": "John",
    "raw": "John",
    "confidence": 0.95
  },
  "orderId": "ED456-G"
}
~~~

### The lifecycle storage

- The memory key is created when the value can be filled by the requirement or through a configuration of an **edit memory action** or through your code, in a webhook call.
- The memory key and the value never change and are never overwritten during all the conversation, unless you configure an update in the **edit memory action**


## How manipulate memory in the platform

The memory can be filled automatically through the requirements, or manually through a configuration of an **edit memory action**.

### Through the requirements

A requirement can be either an *entity* or an *intent* detected in the user input. When you create a requirement, it will automatically be detected and saved in your memory with the key you will choose:

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/1-requirement.png)

* Why the requirement **key** is important and usefull?

- You can reuse an information at different moment in the conversation. If you need the name of your user in two different skills, you have a requirement "#person" (The entity that represent human name) in each of these skills. If this name key is filled by the first skill, the bot will not ask when the discussion will be in the second skill

- Maybe you need to store the same entity "#person" twice but for different purpose. You want the name of your user, and also his dog's name. You will then create a requirement with "#person" saved as "username" and a second requirement with "#person" saved as "dogname".

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/2-requirements.png)


### Through the actions

- clic on "edit memory action"
- You can reset all the memory (erase all the keys) and reset new fields
- You can just set new field and unset others
- Value should be proper JSON

This memory modification are done synchronously, it means if you configure a text message with a variable "Hello {{memory.username}}", then you edit the memory by replacing the value of `username` by `bob`, then you configure a new message "Hello {{memory,username}}", you will have this bot replies:

Hello John (by assuming John was given previously by the user)
Hello bob

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/edit-memory.png)

## How manipulate memory in webhook custom code

You can edit the memory in your code, during a webhook call. Read the (https://recast.ai/docs/concepts/code-and-webhook)[Webhook section] to understand how to format your response.
Here is an example of how to format the return of your webhook call and update the memory of the conversation:

~~~ json
{
  "conversation": {
    "memory": {
      "username": "bob"
    }
  }
}
~~~

<br>

`memory` will replace the actual memory of your bot (so be careful if you just want to change one of your memory keys to add all your other keys so that you don't lose everything).

You can also update the memory through an API call: (https://recast.ai/docs/api-reference/#update-a-conversation)[Check the API reference].

## How start a conversation with memory

You can start a conversation with prefilled information in the memory, and not wait that the first user input is analysed and first skills is triggered.

It's only possible if you are using Bot Builder directly (without Bot Connector). You can read (https://recast.ai/docs/api-reference/#dialog-endpoints)[this section] in the API reference to understand how you need to use the Bot Builder API to do so.
