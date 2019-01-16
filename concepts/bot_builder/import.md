---
layout: concept
title: Import NLP data from other platforms
permalink: /concepts/import
---


Building larger bots can take a long time.
The import should enable you to speed up your bot development process.
To keep the training effort low and make it easier for you to move to our platform you can import intents, expressions, and custom entities.
Currently, we support the CSV- and the JSON format for importing your NLP data.

## Importing synonyms

Each entity can have multiple synonyms.
To import synonyms, you need to specify the actual value of the synonym as well as the iso code indicating to which language the value belongs.

<br><br>

| Key         | Required | Value  | Description                  |
| ----------- | -------- | -------| ---------------------------- |
| value       | Yes      | String | The synonym                  |
| language    | Yes      | String | The iso code of the language |

Please format the CSV file as the following:
(<a href="/assets/import-examples/synonyms.csv" download>Example</a>)

<br>

| value           | language |
| --------------- | -------- |
| NYC             | en       |
| the big apple   | en       |
| la grande pomme | fr       |

<br>

There is a limit for importing synonyms.
You are allowed to import 10,000 synonyms at once, while not exceeding the file size limit of 1 MB.
The import process using the merge option does not get executed if the value of the synonym is already existing.

## Importing expressions

Each expression is defined through the language it is written in and a source/ sentence.

<br><br>

| Key        | Required | Value  | Description                                                 |
| ---------- | -------- | ------ | ----------------------------------------------------------- |
| expression | Yes      | String | A sentence or word group                                    |
| language   | Yes      | String | The iso code representing the language                      |

<br>

Please format the CSV file as the following:
(<a href="/assets/import-examples/expressions.csv" download>Example</a>)

<br>

| expression                | language |
| ------------------------- | -------- |
| I want to travel to NYC.  | en       |
| Let's travel to New York! | en       |

<br>
There is a limit for importing expressions.
You are allowed to import 10,000 expressions at once, while not exceeding the file size limit of 1 MB.
Additionally, you cannot add the same expression multiple times to the same intent.
