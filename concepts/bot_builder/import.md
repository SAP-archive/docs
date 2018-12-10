---
layout: concept
title: Import NLP data from another platform
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

| Key                   | Required | Value
|-----------------------|----------|-------------------------------------------|
| name                  | Yes      | String                                    |
| description           | Optional | String                                    |
| activated             | Optional | Boolean (true by default)                 |

<br>

If you choose to use a JSON file for the import, please format it as the following:
(<a href="/assets/import-examples/intents.json" download>Example</a>)

~~~ json
{
  "intents": [
    {
      "name": "The name of your intent",
      "description": "The description of your intent",
      "activated": true
    }
  ]
}
~~~

<br>

If you choose to use a CSV file for the import, please format it as the following:
(<a href="/assets/import-examples/intents.csv" download>Example</a>)

<br>

| name                    | description                    | activated |
|-------------------------|--------------------------------|-----------|
| The name of your intent | The description of your intent | true      |

<br>
