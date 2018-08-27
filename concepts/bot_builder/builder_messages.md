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

![Recast.AI - Messages types](https://cdn.recast.ai/man/recast-ai-type-of-messages.png)

If your bot is connected to a channel through the Bot Connector, these messages types are adapted to the channel constraint and transformed, so the look and feel will probably change compared with what you see on the Recast.AI platform.

![Recast.AI - Messages types](https://cdn.recast.ai/man/bot-builder/test-card-recast-ai.png)

### Character limits

On the platform, we display a character limit for every message. For example, a text message has a limit of 640 characters. This isn't a real limitation; you can still create a text message with more characters. It serves as an indication based on what Facebook Messenger will accept. So if you're using Messenger, it's a good idea to observe the character limit; otherwise your messages won't be posted in the user's conversation.

### Variables

You can dynamically inject the content gathered from the conversation in the bot replies by using double brace syntax. For example, if your bot asks for the user's name as a requirement, the name is added to the bot's memory once the requirement is completed. You can then create a text message (or any other message actually) filled with "Hello {{memory.username.raw}}", where `{{memory.username.raw}}` is replaced with the actual username.

![Recast.AI - Action](https://cdn.recast.ai/man/recast-ai-action-2.png)

Here's a list of the more useful variables:

* `{{memory.person.raw}}`: A value stored in the memory of the bot. Here, *person* is the alias of a requirement.
* `{{nlp.source}}`: Raw user input
* `{{nlp.entities.location[0]}}`: The first entity detected of the type \`location\`. You can replace \`location\` with any entity name you want.
* `{{nlp.sentiment}}`: <a href="https://recast.ai/docs/api-reference#sentence-sentiments" target="_blank" rel="noopener noreferrer">Sentiment</a> of the sentence
* `{{nlp.intents[0].slug}}`: Slug of the first intent detected
* `{{skill}}`: Slug of the current skill
* `{{skill_occurrences}}`: Number of consecutive occurrences of the current skill

You can create all these variables using information in your [conversation state](https://recast.ai/docs/concepts/conversation-state).


## How to send rich messages from your code

For a list of the rich messages supported and their format, see [Structured messages](https://recast.ai/docs/concepts/structured-messages).

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

For more information, see [Custom code and webhooks](https://recast.ai/docs/concepts/code-and-webhook).
