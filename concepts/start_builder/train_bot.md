---
layout: concept
title: Train your bot
permalink: /concepts/train-your-bot
---

## Create an intent

Everything your chatbot understands is in the intents. Each intent corresponds to an action that your user wants to perform. For example, the intent **greetings** enables your bot to understand when a user says \`Hello\`.

Explore each intent by clicking the name of the intent (for example, **greetings**) and you'll see the expressions inside that train your bot to understand the user's intent.

Let's add a new capability to our chatbot to book a meeting room. Add a new intent called **booking** to understand when users ask your chatbot to book a room. In the **SEARCH** field, type \`booking\` and click **SEARCH** to search and fork this intent from the community. Since the platform is collaborative, many intents have already been created. Select one of the first results and click **FORK**.

![Recast.AI fork intents](https://cdn.recast.ai/man/introduction/search-booking.png)

## Add expressions

Click the intent **booking** that you've just added to your bot. The optimal setting for an intent is to contain around twenty paraphrased expressions. Identify some expressions that your users are likely to say and add each expression to the intent by by entering it in the **Add an expression** field and pressing **Enter**.

![Recast.AI expressions](https://cdn.recast.ai/man/introduction/booking-intent.png)

## Use entities

Go to the intent **booking**. If you click one of the expressions, you'll see highlighted words with tags. These are entities. Entities are keywords detected in expressions that are important to you in order to automate a task.

![Recast.AI intents](https://cdn.recast.ai/man/recast-ai-entitiesb.png)

We automatically detect <a target="_blank" rel="noopener noreferrer" href="https://recast.ai/docs/api-reference#list-of-entities">31 different entities</a> such as *Datetime*, *Location*, *Person*, and so on.
We call them gold entities. If you need another entity – for example, a custom entity like a meal for a cooking bot – just select what you want to tag as your new entity and type a name. The more examples you provide, the better the detection will be.

![Recast.AI tag entities](https://cdn.recast.ai/man/recast-ai-tag-entitiesb.png)

## Test with the NLP console

Once you’ve created new intents, you can test them with the console. To display the console, click **TEST** at the top right of the page. To test if your bot is well-trained, try typing \`I want meeting room 2 for tomorrow\`.

![Recast.AI NLP analyze](https://cdn.recast.ai/man/introduction/console-view.png)

You can see which intent is detected and which entities are extracted. To switch the view to the JSON mode, click the **Smart view** toggle.
The JSON contains a lot of useful information about the message you’ve sent, such as all the enrichments we can provide for the gold entities.

![Recast.AI NLP JSON](https://cdn.recast.ai/man/introduction/console-json.png)

## Train your bot

If your message doesn’t match an intent, you need to train your bot. On the **MONITOR** tab, click the **Log Feed** option to show the logs for your bot. Select the expressions that didn't match an intent and redirect them to the correct intent. Then check that your custom entities have been automatically tagged. If not, tag them and remember *Bot trained, mommy approved!*

![Recast.AI bot monitor](https://cdn.recast.ai/man/introduction/monitor-log-feed.png)
