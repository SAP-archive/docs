---
layout: concept
title: Entity
permalink: /concepts/entity
---

## Definition
An entity is a **keyword** that is extracted from an expression.
We automatically detect <a href="https://recast.ai/docs/concepts/gold-entities" target="_blank" >28 different entities</a> such as Datetime, Location, Person, and so on.
We call them **gold entities**.
However, you're not limited to these gold entities. You can also tag your own **custom entities** to detect keywords depending on your bot's context, such as subway stations if you're building a transport assistant.

## Gold entities

All gold entities are detected automatically. This means that you cannot deactivate them and train them. To bring you a precise service with true added value, we enrich each gold entity with essential core information.
For example, when the gold entity \`tomorrow\` is detected in a sentence, a formatted version of the datetime that you can use as a reply is returned.

~~~ json
{
  "formatted": "Thursday, 06 October 2017 at 09:00:00 AM",
  "iso": "2016-10-06T09:00:00Z",
  "accuracy": "day",
  "chronology": "future",
  "raw": "tomorrow",
  "confidence": 0.92
}
~~~

See all <a target="_blank" rel="noopener noreferrer" href="https://recast.ai/docs/concepts/gold-entities">gold entities</a> and their enrichment.

## Custom entities

You don’t have to tag everything in your expressions. Just annotate what really **needs** to be extracted.
You can use custom entities for three different reasons:

1) You want to detect all possible occurrences of something in a sentence. For example, you're building a transport bot and you want to detect all subway stations.

2) You want to understand if something is present or not in a sentence. 

3) Entities have an influence on intent detection. You can create a custom entity unique to an intent to facilitate this intent’s detection.

Custom entities can be either **free** or **restricted**.

### How free custom entities work

A **free** custom entity is used when you don't have a strict list of values and want machine learning to detect all possible values. For example, you want to detect book titles.

These entities are detected through machine learning. This means that you need to provide examples of the characteristics to train the detection, that is, provide possible values and the way the entity is used in a sentence.

To train a **free** custom entity:

1) In your intent, tag the appropriate words (by highlighting a word or group of words, and adding the entity label). Annotate it in each expression and continue to add expressions until your entity is detected automatically.

![tag entity](https://cdn.recast.ai/man/nlp-lexic/tag-entity.png)

2) You can also provide a list of values for this entity without tagging it in sentences. In Recast.AI, go to *Entities* and just add synonyms. These values are combined with the expressions you annotated to improve the training of our entity detection system. **Caution:** If you provide too many examples of values in this list of synonyms, the algorithm will prioritize the fact that the word is present in this list and will use the information provided by the tagging (like the position of the entity in a sentence, the previous word, the length, and so on).

### How restricted custom entities work

A **restricted** custom entity is used if you have a strict list of words to detect and don't need automatic detection of the entity. No word can be recognized as an entity if it doesn’t appear in a closed list of synonyms. For example, you build a bot to help your customers order pizza. You want to detect all pizza names that your restaurant offers.

To create a **restricted** custom entity:
In Recast.AI, go to *Entities*, click **CREATE**, and select **Restricted entity**. Then add values (synonyms) for this entity. You can also upload a CSV file or use the [gazette endpoint of the API](https://recast.ai/docs/api-reference/#gazettes) to quickly create a large list of synonyms.

![synonyms](https://cdn.recast.ai/man/nlp-lexic/synonym-list.png)

You can define a strictness parameter that is used to determine if a word matches a given value in your list. With a strictness of 100, a word must exactly match an entry of the gazette to be detected as such.

You can still tag a **restricted** custom entity in your sentences, but it will not help entity detection. It will just provide additional information for intent classification.

## References between entities

For users to meaningfully converse with your chatbot using natural language, your bot needs to be able to recognize pronouns (like *it* or *that*) and map them to entities previously mentioned in the conversation. In the following example, the pronoun *it* refers to the entity *Apple USB-C to HDMI dongle*.

<img src='https://cdn.recast.ai/man/nlp-lexic/entity-and-pronoun-example.png' width='380px' />

For your bot to resolve pronouns, you must first go to the **Settings** page for your bot, choose **Options**, and select the **Resolve pronouns** checkbox. (The default setting is not selected.) Selecting this checkbox enables your bot to resolve the following pronouns: she, he, it, we, they, her, him, it, us, them, his, this, that.

<img src='https://cdn.recast.ai/man/nlp-lexic/resolve-pronouns-checkbox.png' width='300px' />

With this checkbox selected, the bot now successfully maps the pronoun *it* to the entity *Apple USB-C to HDMI dongle*.

<img src='https://cdn.recast.ai/man/nlp-lexic/entity-and-pronoun-resolved.png' width='380px' />

The following are not supported:
 
* Split antecedents

  This is where you have more than one entity (for example, *Check whether Harry and Sally are available*) before a pronoun is used that encompasses these multiple entities (for example, *Set up a meeting with them*).
 
* Cataphora

  This is the use of a pronoun that refers to or stands for a subsequent entity (for example, *When she arrives, let Sally know I’ll be waiting in the conference room*). 
 
Remember to set a message that your bot can use if it is unable to map the pronoun to an entity. For example, if your bot is unable to map the pronoun *her* to a person, you might want to set the message *Sorry, can you please name the person?* To do this, first open the skill. Under **Requirements**, click **EDIT REPLIES** next to **If #person is missing** and enter the message.

![Recast.AI gold entities](https://cdn.recast.ai/man/nlp-lexic/edit-replies.png)

![Recast.AI gold entities](https://cdn.recast.ai/man/nlp-lexic/message-example.png)
