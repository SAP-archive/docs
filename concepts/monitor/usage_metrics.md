---
layout: concept
title: Usage metrics
permalink: /concepts/usage-metrics
---

## Are usage metrics available for my bot?

All metrics are extracted from the conversations that users have with your bot through the Bot Builder.
<br><br>

| How you're using the platform | Usage metrics |
| ----------------------------- | ------------- |
| I'm using the Bot Builder and Bot Connector | Available |
| I'm using the Bot Builder directly through the API (with the `/dialog` endpoint) | Available |
| I'm using the NLP API only (with the `/request` endpoint) | Not available |
| I'm using the NLP API and Bot Connector | Not available |

<br>
All metrics are filtered by one of the `languages` of your bot (except for some graphics, where indicated) and a time range that you can select. For quicker loading, the default time range is the previous week. To change the time range, click **SHOW FILTERS**. Also for better loading, the metrics are fetched asynchronously.

## Metrics type

### Conversations

<table>
<tr>
<td width='200px'>
<img class='custom' src='https://cdn.cai.tools.sap/website/bot-analytics/recast-ai-analytics-conversation.svg' width='150px'>
</td>
<td>
<p>
A conversation is a sequence of interactions between your bot and your users. When no new messages appear in the conversation for 10 minutes, we consider the conversation to be over.
The conversation ID can be the same for a user who has 3 conversations with your bot. This happen when your bot is connected to Facebook Messenger. If a user has one long conversation with your bot, we split this long conversation into several parts to understand when the user starts a real new conversation with your bot. 
</p>
</td>
</tr>
</table>

### Users

<table>
<tr>
<td width='200px'>
<img class='custom' src='https://cdn.cai.tools.sap/website/bot-analytics/recast-ai-analytics-users.svg' width='150px'>
</td>
<td>
<p>
A user can have several conversations with a bot. Users are unique by channel. This means that if your bot is connected to two different channels, the same person is considered as user A in the first channel and as user B in the second channel.
</p>
</td>
</tr>
</table>


### Messages received


<table>
<tr>
<td width='200px'>
<img class='custom' src='https://cdn.cai.tools.sap/website/bot-analytics/recast-ai-analytics-one-message.svg' width='150px'>
</td>
<td>
<p>
All messages sent by your users are considered as messages received when the users type a sentence, but also when they click on a button or quick reply.
</p>
</td>
</tr>
</table>


### Average messages by conversation

<table>
<tr>
<td width='200px'>
<img class='custom' src='https://cdn.cai.tools.sap/website/bot-analytics/recast-ai-analytics-average-messages.svg' width='150px'>
</td>
<td>
<p>
Taking all conversations into account, this is the average number of messages received from the user in each conversation.
</p>
</td>
</tr>
</table>

### Most used...

* **Intents**:  How many times intents are detected in all sentences. If multiple intents are detected, each intent is counted.

* **Entities**: How many gold and custom entities are detected in all sentences.

* **Skills**: How many times your skills have been triggered, that is, how many times a user enters a skill and follows the conversation flow, no matter how many interactions the user has in this skill. However, it doesn't mean that the user succeeds in reaching the end of the skill.
