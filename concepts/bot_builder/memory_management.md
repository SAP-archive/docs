## Your conversation memory

Each conversation with a unique user has a memory object from the beginning to the end of the conversation. This memory persists during the entire conversation; you can update it at any time or clear it whenever you want.

When a new conversation starts, the memory is an empty object (unless you want to start a new conversation with prefilled keys). The memory is stored in your <a href="/concepts/conversation-state">conversation state</a>. It is returned in the <a href="/concepts/code-and-webhook#body-configuration">default body</a> of a webhook and after the Bot Builder API call.

For example, your memory object could look like this:
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

### Lifecycle storage

The memory key is created when the value can be filled by the requirement or through a configuration of an **edit memory action** or through your code in a webhook call.

The memory key and value never change and are never overwritten during the entire conversation, unless you configure an update in an **edit memory action**.


## How to manipulate memory in the platform

The memory can be filled automatically through the requirements or manually through a configuration of an **edit memory action**.

### Through the requirements

A requirement can be either an entity or an intent that is detected in the user input. When you create a requirement, it is automatically detected and saved in your memory with the key that you choose:

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/1-requirement.png)

You can reuse information at different moments in the conversation. For example, if you need the name of your user in two different skills, you have a requirement "#person" (the entity that represents the person's name) in each of these skills. If this name key is filled by the first skill, the bot will not ask when the discussion will be in the second skill.

Here's another example: You may need to store the same entity "#person" twice, but for different purposes. You want the name of your user and also his dog's name. You therefore create a requirement with "#person" saved as "username" and a second requirement with "#person" saved as "dogname".

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/2-requirements.png)


### Through an edit memory action

Click "Edit memory action". You have the following options:
- You can reset all the memory (that is, erase all the keys) and reset new fields
- You can just set a new field and unset others

Be sure that the value is proper JSON.

These memory modifications must be done synchronously. For example, if you configure a text message with a variable "Hello {{memory.username}}", then edit the memory by replacing the value of `username` with `Bob`, and then configure a new message "Hello {{memory,username}}", you will have these bot replies:

Hello John (assuming John was given previously by the user)

Hello Bob

![Recast.AI - Requirement](//cdn.recast.ai/man/bot-builder/edit-memory.png)

## How to manipulate memory in webhook custom code

You can edit the memory in your code during a webhook call. To understand how to format your response, see (https://recast.ai/docs/concepts/code-and-webhook)[Custom code and webhooks].
Here's an example of how to format the return of your webhook call and update the memory of the conversation:

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

`memory` will replace the actual memory of your bot (so be careful that you don't lose everything if you just want to change one of your memory keys to add all your other keys).

You can also update the memory through an API call. For more information, see (https://recast.ai/docs/api-reference/#update-a-conversation)[Update a conversation] in the API Reference.

## How to start a conversation with memory

You can start a conversation with prefilled information in the memory, and not wait until the first user input is analyzed and the first skills are triggered. However, this is only possible if you are using the Bot Builder directly (without the Bot Connector). To understand how you need to use the Bot Builder API to do this, see (https://recast.ai/docs/api-reference/#dialog-endpoints)[/Dialog (Text)] in the API Reference.
