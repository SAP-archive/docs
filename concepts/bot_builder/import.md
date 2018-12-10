---
layout: concept
title: Import NLP data from other platforms
permalink: /concepts/import
---


Building bigger bots can take a lot of time.
In order to speed up your bot development process, you can use the import function.
To keep the training effort low and make it easier for you to move to our platform you can import intents, expressions, and your own custom entities.
Currently, we support both: CSV and JSON format for importing your NLP data.

## Importing intents

In order to import intents, you must provide at least a name for each intent.
Furthermore, you can disable an intent or add a description.

<br><br>

| Key         | Required | Value                     | Description                                    |
| ----------- | -------- | ------------------------- | ---------------------------------------------- |
| name        | Yes      | String                    | The name of the intent                         |
| description | Optional | String                    | A short description for what the intent is for |
| activated   | Optional | Boolean (true by default) | A flag to enable/ disable the intent           |

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/intents.json" download>Example</a>)

~~~ json
{
  "intents": [
    {
      "name": "want-food",
      "description": "Intent for ordering groceries",
      "activated": true
    }
  ]
}
~~~

<br>

If you choose to use a CSV file for the import, please format it as the following:
(<a href="/assets/import-examples/intents.csv" download>Example</a>)

<br>

| name      | description                   | activated |
| --------- | ----------------------------- | --------- |
| want-food | Intent for ordering groceries | true      |

<br>

Please be aware that the intent names might be subject to modification.
Furthermore, you can only import max. 10,000 intents at once while the file size must not exceed 1 MB.
The import process does not get executed if an intent with the specified name is already existing.

## Importing expressions

Each expression is defined through the language it is written in and a source/ sentence.
For each word of the expression you can determine the entity the expression belongs to.

<br><br>

| Key      | Required | Value  | Description                                                 |
| -------- | -------- | ------ | ----------------------------------------------------------- |
| source   | Yes      | String | The sentence where each word *can* get linked to an entity  |
| language | Yes      | String | An object containing the iso code representing the language |

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/expressions.json" download>Example</a>)

~~~ json
{
  "expressions": [
    {
      "source": [
        "I",
        "want",
        "to",
        "eat",
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
    }
  ]
}
~~~

<br>

If you choose to use a CSV file for the import, please format it as the following:
(<a href="/assets/import-examples/expressions.csv" download>Example</a>)

<br>

| language | 1   | 2    | 3   | 4   | 5            | 6   |
| -------- | --- | ---- | --- | --- | ------------ | --- |
| en       |  I  | want | to  | eat | cheese\tfood | .   |


*(It is not required to have the words indices in the header.)*

<br>

All specified entity names have to exist before starting the expression import.
Currently, you are allowed to import up to 15,000 expressions at once while not exceeding the file size limit of 1 MB.
Additionally you can add the same expression multiple times to the same intent.

## Importing entities

Each entity consists of an entity-name and can have an open or closed gazette.
If you choose to have an closed gazette you need to specify the strictness of that gazette.

<br><br>

| Key         | Required           | Value                     | Description                                                       |
| ----------- | ------------------ | ------------------------- | ----------------------------------------------------------------- |
| name        | Yes                | String                    | The name of the entity                                            |
| open        | Optional           | Boolean (true by default) | A flag to mark the gazette of the entity as open or closed        |
| strictness  | Partially required | Number within 0-100       | The strictness of the gazette. Only required if gazette is closed |

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

## Importing all together

This import allows you to add intents, expressions and entities at the same time using a single file.
The main difference of this method compared to the others is the way on how the import works.
Instead of rejecting the import file if there is an entity or intent already existing, this one will update the existing ones with the latest import information.
If there is an expression referencing to an entity which is not already existing, the entity will get created.

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/all.json" download>Example</a>)

~~~ json
{
  "entities": [
    {
      "name": "food",
      "open": true
    }
  ],
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
(<a href="/assets/import-examples/all.csv" download>Example</a>)

<br>

| import type |
| ----------- | ------------ | ------------------ | ------------------------ | --- |
| intent      | intent-name  | intent-description | is-activated             |
| entity      | entity-name  | is-open            | strictness               |
| expression  | language-iso | first word         | second word\tentity-name | ... |

<br>
There is a limit for importing intents, expressions and entities you can import at once of 10,000 each, while not exceeding the file size limit of 1 MB.
