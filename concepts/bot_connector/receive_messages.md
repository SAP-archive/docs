---
layout: concept
title: Receive messages
permalink: /concepts/receive-messages
---

When you receive messages from Bot Connector, the body of the request contains various useful information that your bot can leverage to reply to the sender.

## Format

Your bot will receive the message in the same format, no matter what channel it comes from. Here's the content of the message:

~~~ javascript
{
  chatId: 'XXXXXX'
  senderId: 'XXXXXXX',
  mentioned: true,
  origin: 'XXXX',
  message: {
    participant: 'XXXXXX',
    conversation: 'XXXXXX',
    receivedAt: 'XXXXXX',
    attachment: {
      type: 'text',
      content: 'Hello, world!',
    },
  },
}
~~~

## Attributes

Here's the attribute of the payload your bot receive:

| Key         | Value                                 |
| ---         | ------                                |
| chatId      | [String] The channel's native id of the chat   |
| senderId    | [String] The channel's native id of the sender |
| mentioned   | [Boolean] Wether the bot is mentioned or not   |
| origin      | [String] The origin of the message ('messenger', 'slack',...) |
| message     | [Object] The message itself                    |

And here's the exact content of the \`message\` itself:

| Key            | Value                                 |
| -------------- | ------                                |
| participant    | [String] The Id of the participant on Bot Connector                   |
| conversation   | [String] The Id of the conversation on Bot Connector                  |
| receivedAt     | [String] The date at which you received the message                   |
| attachment     | [Object] An object containing the type and the content of the message |
