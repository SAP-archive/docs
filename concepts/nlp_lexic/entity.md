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

You can use custom entities for 3 different reasons:

1) You want to detect all the possible occurences of something in a sentence. Ex: you're building a transport bot, you want to detect all metro station.

2) You want to understand if something is present or not in a sentence. Ex: you're building a 

3) Entities have an influence on the intent detection. You can create a custom entity unique to an intent to facilitate this intent’s detection.

Custom entities can be either **free** or **restricted**.

#### How free custom entities work?

A **free** custom entity is used when you want to detect something that doesn't belong to a closed list of values. 
A **free** custom entity is an entity detected with Machine Learning process. It means that you need to provide examples of what are the characteristics of this entity: possible values, and the way this entity is used in a sentence.


### How restricted custom entities work?

#### How create custom entities

#### Tips
* You don’t have to tag everything in your expressions. Just annotate what's really **needs** to be extracted
* 
* When you create a custom entity, annotate it in each expression, and continue to add expressions until your entity is automatically detected

