---
layout: concept
title: Usage Metrics
permalink: /concepts/usage-metrics
---

## How can I get these metrics for my bot?

All metrics are extracted from the conversations that users have with your bot through Bot Builder.

| How you're using the platform | Usage metrics |
| ----------------------------- | ------------- |
| I'm using Bot Builder and Bot Connector | Available |
| I'm using Bot Builder directly through the API (with the `/dialog` endpoint) | Available |
| I'm using the NLP API only (with the `/request` endpoint) | Not available |
| I'm using the NLP API and the Bot Connector | Not available |

All metrics are filtered by one of the `language` of your bot (unless some graphics, when it's specified) and a time range you can select.

## Metrics type

### Conversations

[Recast.AI - conversations](https://cdn.recast.ai/website/bot-analytics/recast-ai-analytics-conversation.svg)

A conversation is a sequence of interactions between your bot and your users. When no new messages appear in the conversation for 10 minutes, we consider it as finished.
The conversation ID can be still the same for a user who has 3 conversations with your bot. This happen when your bot is connected to Messenger. A user has one big conversation with your bot, but we split this big conversations by several parts to understand when he start a real new conversation with your bot. 

### Users

[Recast.AI - conversations](https://cdn.recast.ai/website/bot-analytics/recast-ai-analytics-users.svg)

A user can have several conversations with a bot. Users are unique by channel. This means that if your bot is connected to two different channels, the same person is considered as user A in the first channel and as user B in the second one.

### Messages received

[Recast.AI - conversations](https://cdn.recast.ai/website/bot-analytics/recast-ai-analytics-one-message.svg)

All messages sent by your users are considered as messages received when the users type a sentence, but also when they click on a button or quick reply.


### Average messages by conversations

[Recast.AI - conversations](https://cdn.recast.ai/website/bot-analytics/recast-ai-analytics-average-messages.svg)

Taking all conversations into account, this is the average number of messages received from the user in each conversation.

### Most used...

* **Intents**:  How many times intents are detected in all sentences. If multiple intents are detected, each one is counted.

* **Entities**: How many of  gold and custom entities detected in all sentences.

* **Skills**: How many times your skills have been triggered, that is, how many times a user "enters" a skill and follows the conversation flow, no matter how many interfactions the user has in this skill. However, it doesn't mean that the user succeeds in reaching the end of the skill.
