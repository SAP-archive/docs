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

---- complete ----


## How manipulate memory in the platform

The memory can be filled automatically through the requirements, or manually through a configuration of **memory actions**.

### Through the requirements

A requirement can be either an *entity* or an *intent* detected in the user input. When you create a requirement, it will automatically be detected and saved in your memory with the key you will choose:

[IMAGE HERE WITH ONE REQUIREMENT]

* Why the requirement **key** is important and usefull?

example conversation ---

### Through the actions


## How manipulate memory in webhook custom code

## How start a conversation with memory
