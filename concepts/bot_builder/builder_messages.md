---
layout: concept
title: Messages
permalink: /concepts/builder_messages
---

## How to create messages on the platform

On the **Actions** tab of a skill (or on the **Requirements** tab), you can choose among other things to send messages.

### Formats
Many different formats are supported, enabling you to build an awesome user experience for your bots. Below is a list of formats and their advantages.

- **Text**: Great for simple informative messages, even if the 640-character limit is pretty high. We recommend keeping them short if you want your users to read them!
- **Card**: Super useful for presenting a product because you can include an image, title, subtitle, and so on.
- **Buttons**: Cool if you want to guide the user in the conversation with a few limited choices.
- **Quick replies**: Same purpose as buttons, but disappear once clicked. Great if you don't want the user to have to scroll up the conversation and click on a button again.
- **Carousel**: A succession of cards that you can scroll from right to left, usually used for presenting multiple products.
- **List**: Same purpose as a carousel, but presented as a vertical list so that you can see everything at once, whereas with the carousel you have to scroll. A list is a little bit smaller than a carousel though, and the images are smaller.
- **Image**: How could you post entertaining GIFs otherwise?!

![SAP Conversational AI - Message types](https://cdn.cai.tools.sap/man/recast-ai-type-of-messages.png)

If your bot is connected to a channel through the Bot Connector, these messages types are adapted to the channel constraint and transformed, so the look and feel will probably change compared with what you see on the SAP Conversational AI platform.

![SAP Conversational AI - Message types](https://cdn.cai.tools.sap/man/bot-builder/test-card-recast-ai.png)

### Character limits

On the platform, we display a character limit for every message. For example, a text message has a limit of 640 characters. This isn't a real limitation; you can still create a text message with more characters. It serves as an indication based on what Facebook Messenger will accept. So if you're using Messenger, it's a good idea to observe the character limit; otherwise your messages won't be posted in the user's conversation.

### Markdown
 
When creating text messages or quick replies, you can opt to use markdown to format text as **bold**, _italics_, or as a [hyperlink](https://cai.tools.sap). This requires you to select the **Enable rich text for this message** checkbox.
 
- For **bold**, add two asterisks (\*\*) or two underscores (\_\_) before and after a word or phrase. For instance, "Tell me what you want, what you \*\*really, really\*\* want" will be rendered as "Tell me what you want, what you **really, really** want".
 
- For _italics_, add a single asterisk (\*) or single underscore (\_) before and after a word or phrase. For instance, "This is how you \_italicize\_ text" will be rendered as "This is how you _italicize_ text".
 
- For [hyperlinks](https://cai.tools.sap), use \[link text](URL)\. For instance, "Find us at \[SAP Conversational AI](https[]()://cai.tools.sap)" will be rendered as "Find us at [SAP Conversational AI](https://cai.tools.sap)". If you don't provide a link text, the URL itself will be rendered as the link. For instance, "Find us at \[](https[]()://cai.tools.sap)" will be rendered as "Find us at [https://cai.tools.sap](https://cai.tools.sap)".
 
For a preview of how your text message or quick reply will be rendered, simply save it.
 
Markdown in the text messages and quick replies that you create in SAP Conversational AI is supported in the following channels:
 
- Facebook Messenger
- Skype
- Slack
- Telegram
- Webchat 
  
If you've connected your bot to a channel that doesn't support bold or italics, the formatting will be removed and replaced with single quotes (') instead of italics, and double quotes (") instead of bold, so that the formatted words are still given special attention. For instance, "Tell me what you want, what you \*\*really, really\*\* want" will be rendered as "Tell me what you want, what you "really, really" want". If a channel doesn't support hyperlinks, the hyperlink will be replaced with "text (URL)", for example, “SAP Conversational AI (https[]()://cai.tools.sap)”.

If you use markdown without selecting the **Enable rich text for this message** checkbox, the characters that you entered will be passed to the channel exactly as you entered them.

### Message delay

You can add a delay of up to 5 seconds between each message in a group of messages.

The main reason for adding a delay is so that users have enough time to read the message before your bot sends the next one. In a chat interface, this is especially important because each new message moves the previous message up. Also, dropping several messages with no delay can feel a little ... robotic! Another important reason for adding a delay is to give your bot personality. For example, you might want to add a short delay to make it look as though your bot is thinking! But be careful not to make your delays too long, so that users aren't waiting unnecessarily.

![SAP Conversational AI - Specific delay](https://cdn.cai.tools.sap/man/recast-ai-specific-delay.png)

In the screenshot above, the second message will be sent to the user 2 seconds after the first message.

In your bot settings, you can also configure a default delay that is used if you don't set a specific delay.

![SAP Conversational AI - Default delay](https://cdn.cai.tools.sap/man/recast-ai-default-delay.png)

If you don't set any delay, the messages are sent consecutively as usual.

### Variables

You can dynamically inject the content gathered from the conversation in the bot replies by using double brace syntax. For example, if your bot asks for the user's name as a requirement, the name is added to the bot's memory once the requirement is completed. You can then create a text message (or any other message actually) filled with "Hello {{memory.username.raw}}", where `{{memory.username.raw}}` is replaced with the actual username.

![SAP Conversational AI - Action](https://cdn.cai.tools.sap/man/recast-ai-action-2.png)

You can create all of the following variables:

* `{{conversation_id}}`: ID of the current conversation.
* `{{participant_data}}`: An object filled with participant information that is provided by the channel connected through the Bot Connector. For example, for those channels that supply a username, it is returned as `userName`. You can easily use `{{participant_data.userName}}`.
* `{{memory}}`: The complete memory object. You can access each element like `{{memory.person.raw}}`. Here, *person* is the alias of a requirement.
* `{{skill_occurences}}`: Number of consecutive occurrences of the current skill.
* `{{language}}`: Language ISO code of the current conversation.
* `{{current_message}}`: The message source sent by the user.
* `{{#entity}}`: An alias of the `nlp.entities` object. You can access each element like `{{#entity.confidence}}` where `confidence` is `nlp.entities.confidence`.
* `{{message_received_at}}`: Timestamp of when the message was received.
* `{{nlp}}`: The full `nlp` object. You can access any property of it like `{{nlp.sentiment}}` for example if you want to get the `sentiment` property.

### Context management

For users to meaningfully converse with your bot using natural language, your bot can recognize pronouns (like _it_ or _that_) and map them to entities previously mentioned in the conversation. Similarly, if a user uses a superlative like _cheapest_ or _most expensive_, or an ordinal like _first_ or _second_, your bot can map the superlative or ordinal to an item in the message. For more information, and in particular, how to enable this in your bot, see [Entities](https://cai.tools.sap/docs/concepts/entity) and scroll down to _References between entities_. 

## How to send rich messages from your code

For a list of the rich messages supported and their format, see [Structured messages](https://cai.tools.sap/docs/concepts/structured-messages).

Sometimes, you want to interact with a database or external API before sending a reply to the user.
To achieve that, you can create a **CALL WEBHOOK** action to interact with your own code, implement your own logic, and send back the responses built from the data you've gathered. Here's a JS snippet as an example. It assumes that you have a CALL WEBHOOK action calling your `/do_some_stuff` route.

~~~ js
const express = require('express')
const bodyParser = require('body-parser')

const app = express()
const port = 5000
app.use(bodyParser.json())

app.post('/do_some_stuff', (req, res) => {

  // Do your actual logic here

  res.send({
    replies: [{
      type: 'text',
      content: 'Roger that',
    }],
  })
})

app.post('/do_more_complicated_stuff', (req, res) => {

  // Do your actual logic here

  res.send({
    replies: [{
      type: 'text',
      content: 'Roger that',
    }, {
      type: 'picture',
      content: 'The URL of my great GIF that I want to share with the world',
    }, {
      type: 'quickReplies',
      content: {
        title: 'My quick reply title',
        buttons: [{
          title: 'Choice 1',
          value: 'choice 1',
        }, {
          title: 'Choice 2',
          value: 'Choice 2'
        }],
      },
    }],
  })
})

app.listen(port, () => {
  console.log('Server is running on port 5000')
})
~~~

For more information, see [Custom code and webhooks](https://cai.tools.sap/docs/concepts/code-and-webhook).
