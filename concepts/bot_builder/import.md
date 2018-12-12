---
layout: concept
title: Import NLP data from other platforms
permalink: /concepts/import
---


Building bigger bots can take a lot of time.
In order to speed up your bot development process, you can use the import function.
To keep the training effort low and make it easier for you to move to our platform you can import intents, expressions, and your own custom entities.
Currently, we support both: CSV and JSON format for importing your NLP data.

## Importing entities

Each entity consists of an entity-name and can have an open or closed gazette.
If you choose to have a closed gazette you need to specify the strictness of that gazette.

<br><br>

| Key         | Required           | Value                     | Description                                                       |
| ----------- | ------------------ | ------------------------- | ----------------------------------------------------------------- |
| name        | Yes                | String                    | The name of the entity                                            |
| open        | Optional           | Boolean (true by default) | A flag to mark the Gazette of the entity as open or closed        |
| strictness  | Partially required | Number within 0-100       | The strictness of the Gazette. Only required if gazette is closed |

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/entities.json" download>Example</a>)

~~~ json
{
  "entities": [
    {
      "name": "food",
      "open": false,
      "strictness": 90
    }
  ]
}
~~~

<br>

If you choose to use a CSV file for the import, please format it as the following:
(<a href="/assets/import-examples/entities.csv" download>Example</a>)

<br>

| name | open  | strictness |
| ---- | ----- | ---------- |
| food | false | 90         |

<br>

Please be aware that the entity names might be subject to modification.
Furthermore, you can only import max. 5,000 intents at once while the file size must not exceed 1 MB.
The import process does not get executed if an entity with the specified name is already existing.

## Importing intents and expressions

This import allows you to add intents and expressions at the same time using a single file.
In order to import intents, you must provide at least a name for each intent.
Furthermore, you can disable an intent or add a description.
Each expression is defined through the language it is written in and a source/ sentence.
For each word of the expression, you can determine the entity, the expression belongs to.
The import will update existing intents to reflect the state of the latest entry in the import file.
If there is an expression referencing to an entity which is not already existing, the entity will get created.

<br>
*Attributes for intents*
<br>

| Key         | Required | Value                     | Description                                    |
| ----------- | -------- | ------------------------- | ---------------------------------------------- |
| name        | Yes      | String                    | The name of the intent                         |
| description | Optional | String                    | A short description of what the intent is for  |
| activated   | Optional | Boolean (true by default) | A flag to enable/ disable the intent           |

<br>


<br>
*Attributes for expressions*
<br>

| Key      | Required | Value  | Description                                                 |
| -------- | -------- | ------ | ----------------------------------------------------------- |
| source   | Yes      | String | The sentence where each word *can* get linked to an entity  |
| language | Yes      | String | The iso code representing the language                      |

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/intents_and_expressions.json" download>Example</a>)

~~~ json
{
  "intents": [
    {
      "name": "want food",
      "expressions": [
        {
          "source": [
            "I want to eat",
            {
              "raw": "cheese",
              "entity": {
                "name": "food"
              }
            },
            "."
          ],
          "language": {
            "isocode": "en"
          }
        },
        {
          "source": [
            "I'm hungry I would love",
            {
              "raw": "Pizza",
              "entity": {
                "name": "food"
              }
            }
          ],
          "language": {
            "isocode": "en"
          }
        }
      ]
    }
  ]
}

~~~

<br>

If you choose to use a CSV file for the import, please format it as the following:
(<a href="/assets/import-examples/intents_and_expressions.csv" download>Example</a>)

<br>

| import type |
| ----------- | ------------ | ------------------ | ------------------------ | ------------------------ | --- |
| intent      | intent-name  | intent-description | is-activated             |
| expression  | intent-name  | language-iso       | first word               | second word\tentity-name | ... |

<br>
Please be aware that the intent names might be subject to modification.
There is a limit for importing intents, expressions and entities you can import at once of 10,000 each, while not exceeding the file size limit of 1 MB.
Additionally, you can add the same expression multiple times to the same intent.
