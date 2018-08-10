---
layout: concept
title: Messages
permalink: /concepts/builder_messages
---

## How can I create my messages on the platform

In the Action section of your skills (or in your requirements), you can choose among other things to send messages.

### List of formats
Various format exists, so you can build an awesome UX for your bots.

List of formats and their advantages:
- text (great for simple informative messages, even if the limit of characters is pretty high (640), keep them short if you want your users to read them)
- card (super useful for presenting a product, as you can put an image, a title, a subtitle,...)
- buttons (cool if you want to guide the user in the conversation with a few limited choices)
- quick replies (same purpose as the buttons, but will disappear once clicked on. Great if you don't want the user to go up in the conversation and click on a button again)
- carousel (a succession of carousel that you can scroll from right to left, usually used for presenting multiple products)
- list (same purpose as a carousel, but is presented as a vertical list so you can see everything at once, whereas with the carousel you have to scroll. A little bit tinyier than the carousel though, and the images are smaller)
- image (how could you post entertaining GIFs otherwise?)

![Recast.AI - Messages types](https://cdn.recast.ai/man/recast-ai-type-of-messages.png)

If your bot is connected to a channel through Bot Connector, these messages type will be adapted to the channel constraint and transformed, so the look and feel will probably change compared as what you see on the Recast.AI platform.

![Recast.AI - Messages types](https://cdn.recast.ai/man/bot-builder/test-card-recast-ai.png)

### Limitations

On the platform, we display a limit of characters for every messages. For example, a text message has a limitation of 640 chars.

It's not a real limitation, you can still create a text message with more chars. It serves as an indication based on what
Messenger accept.

So if you're using Messenger, it's a good idea to follow them, otherwise your messages won't be posted in the user's conversation

### Variables

You can dynamically inject the content gathered from the conversation in the bot replies by using the double braces syntax.

Ex: your bot asks for the user's name as a requirement. Once the requirement completed, you will have
the name in the memory of the bot.

You can then create a text message (or every other messages actually) filled with: "Hello {{memory.username.raw}}".
Then `{{memory.username.raw}}` will be replaced with the actual username.

![Recast.AI - Action](https://cdn.recast.ai/man/recast-ai-action-2.png)

Here is a list of the more useful variables injection:

* **{{memory.person.raw}}**: a value stored in the memory of the bot. Here *person* is the alias of a requirement
* **{{nlp.source}}**: raw user input.
* **{{nlp.entities.location[0]}}**: first entity detected of the type \`location\`. You can replace \`location\` by any entity name you want.
* **{{nlp.sentiment}}**: <a href="https://recast.ai/docs/api-reference#sentence-sentiments" target="_blank" rel="noopener noreferrer">sentiment</a> of the sentence
* **{{nlp.intents[0].slug}}**: slug of the first intent detected
* **{{skill}}**: slug of the current skill
* **{{skill_occurrences}}**: number of consecutive occurrences of the current skill

All these variables can be created by using information in your [Conversation state](https://recast.ai/docs/concepts/conversation-state).


## How can I send rich messages from my code?

The list of the rich messages supported and their format [can be found here](https://recast.ai/docs/concepts/structured-messages)

Sometimes you want to interact with a database, or with an external API before sending back some replies to the user.
To achieve that, you will want to create a "CALL WEBHOOK" action to interact with your own code, implement your own logic, and send back the responses built from
the data you've gathered.

Here's a JS snippet of how to achieve that, assuming that you have a CALL WEBHOOK action calling your `/do_some_stuff` route:

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

Check how Webhook works: https://recast.ai/docs/concepts/code-and-webhook
