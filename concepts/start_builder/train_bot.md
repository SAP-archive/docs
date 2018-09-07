---
layout: concept
title: Train your bot
permalink: /concepts/train-your-bot
---

## Create an intent

Everything your chatbot understands is in the intents. Each intent corresponds to one action your user wants to perform. For example, an intent **greetings** makes your bot understand when a user says \`Hello\`.

Explore each intent a little bit by clicking on the name and you will see expressions inside that train your bot to understand the user intent ;)

Let's add a new capability to our chatbot to book meeting room. Add a new intent called **Booking**, to understand when users will ask to book a room to your chatbot! Type \`booking\` in the input Search then click on the **Search button** and Fork from the community, .

As the platform is collaborative, there are a lot of intents already created. Select one of the first results and just click on the **FORK** button on the right.

![Recast.AI fork intents](https://cdn.recast.ai/man/introduction/search-booking.png)

## Add expressions

You have a new intent in your bot! Click on it. The optimal setting for a great intent is to contain around twenty paraphrased expressions. Add some expressions your users will say by typing the sentence in the field **Add an expression**.

![Recast.AI expressions](https://cdn.recast.ai/man/introduction/booking-intent.png)

## Use entities

If you click on one of the expressions you will see highlighted words, with tags. These are **entities**. They’re keywords detected in expressions that are important to you in order to automate a task.

![Recast.AI intents](https://cdn.recast.ai/man/recast-ai-entitiesb.png)

We automatically detect <a target="_blank" rel="noopener noreferrer" href="https://recast.ai/docs/api-reference#list-of-entities">31 different entities</a> such as datetimes, names, locations, etc.
We call them gold entities. If you need another entity, a custom one like a **meal** for a cooking bot, just select what you want to tag as your new entity and type a name. The more examples you provide, the better the detection will be ;)

![Recast.AI tag entities](https://cdn.recast.ai/man/recast-ai-tag-entitiesb.png)

## Use the NLP console

Once you’ve created new intents, you can test it with the console. Click on the **TEST** bubble icon on the top right to make it appear. Type a sentence to test if your bot is well trained: \`I want meeting room 2 for tomorrow\`

![Recast.AI NLP analyze](https://cdn.recast.ai/man/introduction/console-view.png)

You will see which intent is detected and which entities are extracted. Click on the **Smart view** toggle to switch the view to the JSON mode.
The JSON contains a lot of useful information about the message you’ve sent, like all the enrichments we can provide for the gold entities.

![Recast.AI NLP JSON](https://cdn.recast.ai/man/introduction/console-json.png)

## Train your bot

When your message doesn’t match any intent, you have to train your bot. Go to the **MONITOR** tab on your bot page, and click on the **Log feed** menu.
Here are the logs of your bots. Select the expressions that did not match and redirect them to the right intent. After that, check that your custom entities have been automatically tagged. If not, do it and remember “Bot trained, mommy approved!”.

![Recast.AI bot monitor](https://cdn.recast.ai/man/introduction/monitor-log-feed.png)
