---
layout: concept
title: Gazette
permalink: /concepts/gazette
---

## Definition
A gazette is a **list of words** that belong to an entity. You can define your own gazettes for your custom entities to improve the quality of the entity recognition.

A gazette can either be **open** or **closed**:
* an **open** gazette will be combined with the expressions you annotated to improve the training of our entity detection system for the entities which possess a gazette.
* a **closed** gazette will not require the training of our entity detection system, and will ensure that no word can be recognized as an entity if it doesn't appear in the gazette.

For each gazette, you can define a strictness parameter that will be used to determine if a word matches a given value in your gazette.

## Tips
* Closed gazettes are useful to exhaustively list possible values for your entity
* With a strictness of 100, a word must exactly match an entry of the gazette to be detected as such
* To bootstrap your entity training, you can follow this process:
  * Upload a closed gazette
  * Add sentences, entities inside them will be detected with the gazette
  * Set the gazette as open, the annotations done at the last step will be used by our entity detection system in conjunction with now opened gazette

## Example
You can import a gazette using a .csv file following these requirements:

A gazette for the \`cheese\` entity:
\`\`\`
"value";"language"
"mozzarella";"fr"
"gouda;"fr"
\`\`\`
