---
layout: concept
title: Entity
permalink: /concepts/entity
---

### Definition
An entity is a **keyword** extracted from an expression.
We automatically detect <a href="https://recast.ai/docs/api-reference#list-of-entities" target="_blank" >31 different entities</a> such as datetimes, names, locations, etc.
We call these **Gold entities**.

But you are not limited to these Gold entities: you can also tag your own **custom** entities to detect keywords depending on your bot's context, such as metro stations if you are building a transport assistant.

### Gold Entities

All gold entities are automatically detected, it means that you can not de-activate them and train them. To bring you a precise service with true added value, we enrich each and every one of our Gold entities with essential core information.

When \`tomorrow\` is detected in a sentence, since it's a gold entity, a formatted version of the datetime that you can use as a reply is returned.

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

See all <a target="_blank" rel="noopener noreferrer" href="https://recast.ai/docs/api-reference#list-of-entities">gold entities</a> and their enrichment.

### Custom Entities

You don’t have to tag everything in your expressions. Just annotate what's really **needs** to be extracted.
You can use custom entities for 3 different reasons:

1) You want to detect all the possible occurences of something in a sentence. Ex: you're building a transport bot, you want to detect all metro station.

2) You want to understand if something is present or not in a sentence. Ex: you're building a 

3) Entities have an influence on the intent detection. You can create a custom entity unique to an intent to facilitate this intent’s detection.

Custom entities can be either **free** or **restricted**.

#### How free custom entities work?

A **free** custom entity is used when you don't have a strict list of values and want machine learning to detect all possible values. For example, you want to detect book titles.

These entities are detected with Machine Learning process. It means that you need to provide examples of what are the characteristics to train the detection: possible values, and the way the entity is used in a sentence.

To train a **free** custom entity:
1) In your intent, tag (by highlighting a word or a group of word, and add the entity label) the appropriate words. Annotate it in each expression, and continue to add expressions until your entity is automatically detected.

[tag entity](https://cdn.recast.ai/man/nlp-lexic/tag-entity.png)

2) You can also provide a list of values for this entity without tagging it in sentences. Go in the *Entities* section, and here you can just add synonyms. These values will be combined with the expressions you annotated to improve the training of our entity detection system. Be carefull, if you provide too much examples of values in this synonyms list, the algorythm will prioritize the fact that the word is present in this list and will use the information provided by the tagging (like the place of the entity in a sentence, the previous word, the length...).

### How restricted custom entities work?

A **restricted** custom entity is used if you have a strict list of words to detect and don't need automatic detection of the entity. No word can be recognized as an entity if it doesn’t appear in a closed list of synonyms. For example, you build a bot to help ytour customers order pizza. You want to detect all the pizza name that your restaurant provide.

To create a **restricted** custom entity, go in the *Entities* section, click on **CREATE** and select the **restricted** option. Then add values (synonyms) for this entity. You can also upload a CSV file, or use the [gazette endpoint of the API](https://recast.ai/docs/api-reference/#gazettes) to create a big list of synonyms faster.

[IMAGE]

You can define a strictness parameter that will be used to determine if a word matches a given value in your list. With a strictness of 100, a word must exactly match an entry of the gazette to be detected as such

You can still tag **restricted** custom entity in your sentences, but it will not help your entity detection. It will just provide additional information for the intent classification.


