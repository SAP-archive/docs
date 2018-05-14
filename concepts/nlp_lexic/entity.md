---
layout: concept
title: Entity
permalink: /concepts/entity
---

### Definition
An entity is a **keyword** extracted from an expression. We automatically detect 31 different entities such as datetimes, names, locations, etc. We call these **Gold entities**.
But you are not limited to these Gold entities: you can also tag your own **custom** entities to detect keywords depending on your bot's context, such as metro stations if you are building a transport assistant.
To bring you a precise service with true added value, we enrich each and every one of our Gold entities with essential core information.

### Tips
* You don’t have to tag everything in your expressions. Just annotate what's really **needs** to be extracted
* Entities have an influence on the intent detection. You can create a custom entity unique to an intent to facilitate this intent’s detection
* When you create a custom entity, annotate it in each expression, and continue to add expressions until your entity is automatically detected

### Example
When \`tomorrow\` is detected in a sentence, a formatted version of the datetime that you can use as a reply is returned.

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

See all [gold entities](https://recast.ai/docs/api-reference#list-of-entities).
