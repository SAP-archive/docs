---
layout: concept
title: Text analysis API
permalink: /concepts/text-analysis-nlp
---

<style>
  .language-javascript,
  .language-python,
  .language-ruby,
  .language-php {
    display: none;
  }

  .highlight {
    padding: 0.5rem;
  }

  .snippet-tab {
    padding: 0.2rem 0.5rem;
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
    background-color: grey;
    color: white;
    cursor: pointer;
  }

  .snippet-tab-active {
    background-color: #002b36;
  }

  .snippet-active {
    display: block !important;
  }

  .code {
    background-color: lightgrey;
    padding: 0.2rem;
    border-radius: 3px;
  }
</style>

## Definition

Text analysis works with any raw text.

<span class='label label-post'>POST</span> `https://api.recast.ai/v2/request`

| Name | Type | Description | Constraints |
| -----| ---- | ----------- | -------- |
| `text` | `String` | This is your user input | Required, not empty, not blank, less than 512 characters |
| `language` | `String` | The language Recast.AI will process your text with | Optional, must be `en`, `fr` or `es` for premium languages, or `ar`, `ca`, `da`, `de`, `fi`, `hi`, `it`, `ja`, `ko`, `no`, `nl`, `pl`, `pt`, `ru`, `sv` and `zh` for standard level languages. If not provided a language detection will be performed | 

## Usage

Copy-paste this snippet in a file by replacing the REQUEST_TOKEN by your token, install the dependencies, and run the file ;)

JS:
<span class="code">npm install recastai</span>

Python:
<span class="code">pip install recastai</span>

Ruby:
<span class="code">gem install RecastAI</span>

PHP:
<span class="code">composer require recastai/sdk-php</span>

<br/>

<script>
  function activateHelloSnippet(language) {
    document.querySelectorAll(".snippet-tab")
      .forEach(elem => elem.classList.remove("snippet-tab-active"));
    document.getElementById(`hello-snippet-${language}`).classList.add("snippet-tab-active")

    for (const lng of ["javascript", "ruby", "python", "php"]) {
      if (lng === language) {
        document.querySelector(`.language-${language}`).classList.add("snippet-active")
      } else {
        document.querySelector(`.language-${lng}`).classList.remove("snippet-active")
      }
    }
  };

  document.addEventListener("DOMContentLoaded", () => {
    activateHelloSnippet("javascript")
  });
</script>

<div id="hello-snippet-container">
  <div class="snippet-tabs">
    <button onclick="activateHelloSnippet('javascript')" id="hello-snippet-javascript" class="snippet-tab">JS</button>
    <button onclick="activateHelloSnippet('ruby')" id="hello-snippet-ruby" class="snippet-tab">Ruby</button>
    <button onclick="activateHelloSnippet('python')" id="hello-snippet-python" class="snippet-tab">Python</button>
    <button onclick="activateHelloSnippet('php')" id="hello-snippet-php" class="snippet-tab">PHP</button>
  </div>
</div>

~~~ javascript
const recastai = require('recastai')

const client = new recastai.request('YOUR_REQUEST_TOKEN', 'en')

client.analyseText('hello')
  .then(function(res) {
    if (res.intent()) { console.log('Intent: ', res.intent().slug) }
    if (res.intent().slug === 'YOUR_EXPECTED_INTENT') {
      // Do your code...
    }
  })
~~~

~~~ ruby
require 'recastai'

client = RecastAI::Client.new('YOUR_REQUEST_TOKEN', 'en')

# text request
response = client.request.analyse_text('hello')
puts response.intent.slug if response.intent
if response.intent.slug == 'YOUR_EXPECTED_INTENT'
  # Do your code...
end
~~~

~~~ python
from __future__ import print_function
import recastai

client = recastai.Client('YOUR_REQUEST_TOKEN', 'en')
response = client.request.analyse_text('hello')

if response.intent:
  print(response.intent.slug)
if response.intent.slug == 'YOUR_EXPECTED_INTENT':
  """Do your code..."""
~~~

~~~ php
<?php
require 'vendor/autoload.php';

use RecastAI\Client;

$client = new Client('YOUR_REQUEST_TOKEN', 'en');

$res = $client->request->analyseText('hello');

if ($res->intent()->slug == 'YOUR_EXPECTED_INTENT') {
	// Do your code
}

?>
~~~

## Response

We return a JSON containing your sentences and actionable data extracted from them.

~~~ json
{
  "results": {
    "uuid": "21ec79d8-3865-40e3-be8b-f31d040efed8",
    "source": "What'll be the weather in London next Thursday?",
    "intents": [
      {
        "slug": "weather",
        "confidence": 0.95
      }
    ],
    "act": "wh-query",
    "type": "desc:desc",
    "sentiment": "neutral",
    "entities": {
      "location": [
        {
          "formatted": "London, UK",
          "lng": -0.1277583,
          "lat": 51.5073509,
          "type": "locality",
          "place": "ChIJdd4hrwug2EcRmSrV3Vo6llI",
          "raw": "London",
          "confidence": 0.99
        }
      ],
      "datetime": [
        {
          "formatted": "Thursday, 06 October 2016 at 09:00:00 AM",
          "iso": "2016-10-06T09:00:00Z",
          "accuracy": "day",
          "chronology": "future",
          "raw": "next Thursday",
          "confidence": 0.95
        }
      ]
    },
    "language": "en",
    "version": "2.4.0",
    "timestamp": "2016-09-30T10:29:54.211866Z",
    "status": 200
  },
  "message": "Resource rendered with success"
}
~~~

<br/>

| Name | Type | Description |
| -----| ---- | ----------- |
| `uuid` | `String` | The universally unique id for this request |
| `source` | `String` | The text we processed |
| `intents` | `Array` of intent | The intents we found, sorted by probability |
| `intent.slug` | `String` | The slug of the intent which matched |
| `intent.confidence` | `Float` | The matching score of the intent |
| `act` | `String` | The act of the request, more info in the [glossary](https://recast.ai/docs/api-reference/#sentence-types) |
| `type` | `String` | The type of the request, more info in the [glossary](https://recast.ai/docs/api-reference/#sentence-types) |
| `sentiment` | `String` | The sentiment of the request, more info in the [glossary](https://recast.ai/docs/api-reference/#sentence-types) |
| `entities` | `Object` | Every keys are in an array of entity, more info in the [glossary](https://recast.ai/docs/api-reference/#sentence-types) |
| `language` | `String` | The language detected (or given) from the processed sentence, follows the [ISO 639-1](https://www.iso.org/iso-639-language-codes.html) standard |
| `version` | `String` | The version of our JSON, follows the [Semantic Versioning Specification](https://semver.org/) |
| `timestamp` | `String` | The UTC timestamp at the end of our processing, follows the [ISO 8061](https://www.iso.org/iso-8601-date-and-time-format.html) standard |
| `status` | `Integer` | The status of our Natural Language processor |

## Errors

We return an error (`400: bad_request`) if any of these cases is met:

* Parameter `text` is missing
* Parameter `text` is blank
* Parameter `text` is longer than 512 characters
* Parameter `language` is neither a standard level language isocode or a premium language isocode

We return an error (`401: unauthorized`) if the following case is met:

* The token provided in your request is not linked to any of your bots.

We return an error (`503: service_unavailable`) if any of these cases is met:

* Our natural language processing service is unavailable

