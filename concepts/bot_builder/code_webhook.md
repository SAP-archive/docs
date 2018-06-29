---
layout: concept
title: Custom code and webhook
permalink: /concepts/code-and-webhook
---


At many points in your conversation, you most likely want to retrieve business information or connect to an external system to perform actions. You can do this through **webhooks**.
A webhook is a simple HTTP call to your backend. To configure your HTTP call, click Webhook action in the Bot Builder.

[IMAGE HERE]

You can provide the full URL or route (starting with a '/') to be called by the Bot Builder. 
If you provide a route, the 'Bot webhook base URL' (configurable in your bot's settings) will be prepended to it.


[IMAGE HERE]

You can specify the HTTP method to use in your webhook call (GET, POST, PUT, DELETE, or PATCH).

[IMAGE HERE]

## Authentication configuration

You have the following options:
•	No authentication: No authentication/authorization is passed with the request.
•	Basic authentication: A username/password pair is passed with the request. 

[IMAGE HERE]

## Header configuration

HTTP headers are accommodated by configuring a key-value pair, where you can name keys and set a value to be passed along in the header.

[IMAGE HERE]

## Body configuration

The HTTP request body must be formatted as a standard JSON object. You can either receive the default body that we provide with all the conversation state or create your own custom body.

The default body format is the following:

~~~ json
{
  "conversation": {
    "id": "A_CONVERSATION_ID",
    "language": "en",
    "memory": {
      "person": {
        "fullname": "Francois",
        "raw": "Francois",
        "confidence": 0.95
      }
    },
    "skill_stack": ["get-weather"],
    "skill": "small-talk",
    "skill_occurences": 1
  },
  "nlp": {
    "source": "hi",
    "intents": [
      {
        "slug": "greetings",
        "confidence": 0.99
      }
    ],
    "sentiment": "vpositive",
    "entities": {},
    "act": "assert",
    "type": null,
    "version": "2.10.1",
    "processing_language": "en",
    "language": "en",
    "uuid": "96597974-3ee1-4743-8a5d-341b67effb9a"
    "status": 200,
    "timestamp": "2017-10-25T21:36:02.071243+00:00",
  }
}
~~~

In custom HTTP request bodies, conversation variables (like memories variables, nlp information..) can be referenced in place of hard-coded values, for example, `{{memory.person.raw}}`.

[IMAGE HERE]

## Templates

You can reuse specific configurations of authorizations, headers, and bodies in other skills by choosing Templates in the skill view. These templates can be managed on the Templates tab.

[IMAGE HERE]

## How to format the response of the webhook call?

The body format of your response should be a valid JSON and can contain two key: `replies` and `conversation`.

| Key                   | Required | Value
|-----------------------|----------|-------------------------------------------|
| replies               | optional | Array of object                           |
| conversation          | optional | Object with a key `memory` and `language` |
| conversation.memory   | optional | Object filled as you want                 |
| conversation.language | optional | String with a language iso format         |

Here is an example:

~~~ json
{
  "replies": [
    {
      "type": "text",
      "content": "Hello world!"
    }
  ],
  "conversation": {
    "language": "en",
    "memory": {
      "user": "Bob"
    }
  }
}
~~~

The `conversation` data you send back will update the state of your conversation:

* the `memory` will replace the actual memory of your bot (so be carreful if you just want to change one of your memory key to add all your others key to not losing everything).
* the `language` will update the language of the conversation: each new sentence sent by the user will be processed in this language and the bot will reply in this language.

The `replies` are send in the body of the result of the main Bot Builder and will appear in the `messages` key:

POST `https://api.recast.ai/build/v1/dialog`

~~~ json
{
    "messages": [
        {
             "type": "text",
             "content": "Hello world!"
        }
    ],
    "conversation": {
        "id": "CONVERSATION_ID",
        "language": "en",
        "memory": {},
        "skill": "default",
        "skill_occurences": 1
    },
    "nlp": {
        "uuid": "b96bc782-6aba-4fac-aeaa-2326936b08bf",
        "source": "Hello Recast.AI",
        "intents": [
            {
                "slug": "greetings",
                "confidence": 0.99
            }
        ],
        "act": "assert",
        "type": null,
        "sentiment": "neutral",
        "entities": {},
        "language": "en",
        "processing_language": "en",
        "version": "2.10.1",
        "timestamp": "2017-10-19T13:24:12.984856+00:00",
        "status": 200
    }
}
~~~


## How to format the array of replies?

Objects in the array of reply can be formatted as you want, depending on your needs when you request the Bot Builder API.
**If you are using Bot Connector**, meaning you have connected a channel on the Recast.AI platform like Facebook Messenger, Slack or a Webchat, you need to follow the format of Bot Connector:  **<a href="/concepts/structured-messages">Check the format to send rich messages</a>**

~~~ json
{
  "replies": [
    {
      "type": "text",
      "content": "Hello world!"
    }
  ]
}
~~~



## How looks your code?

Copy-paste this snippet in a file, install the dependencies and run the file.

JS:
<span class="code">npm install express body-parser --save</span>

Python:
<span class="code">pip install flask</span>

Ruby:
<span class="code">gem install sinatra</span>

PHP:
<span class="code">composer require slim/slim</span>

<br/>

<script>
  function activateWebhookSnippet(language) {
    document.querySelectorAll(".snippet-tab")
      .forEach(elem => elem.classList.remove("snippet-tab-active"));
    document.getElementById(`webhook-snippet-${language}`).classList.add("snippet-tab-active")

    for (const lng of ["javascript", "ruby", "python", "php"]) {
      if (lng === language) {
        document.querySelector(`.language-${language}`).classList.add("snippet-active")
      } else {
        document.querySelector(`.language-${lng}`).classList.remove("snippet-active")
      }
    }
  };

  document.addEventListener("DOMContentLoaded", () => {
    activateWebhookSnippet("javascript")
  });
</script>

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

<div id="webhook-snippet-container">
  <div class="snippet-tabs">
    <button onclick="activateWebhookSnippet('javascript')" id="webhook-snippet-javascript" class="snippet-tab">JS</button>
    <button onclick="activateWebhookSnippet('ruby')" id="webhook-snippet-ruby" class="snippet-tab">Ruby</button>
    <button onclick="activateWebhookSnippet('python')" id="webhook-snippet-python" class="snippet-tab">Python</button>
    <button onclick="activateWebhookSnippet('php')" id="webhook-snippet-php" class="snippet-tab">PHP</button>
  </div>
</div>

~~~ javascript
const express = require('express')
const bodyParser = require('body-parser')

const app = express()
const port = 5000
app.use(bodyParser.json())

app.post('/', (req, res) => {
  console.log(req.body)

  res.send({
    replies: [{
      type: 'text',
      content: 'Roger that',
    }],
    conversation: {
      memory: { key: 'value' }
    }
  })
})

app.post('/errors', (req, res) => {
  console.log(req.body)
  res.send()
})

app.listen(port, () => {
  console.log('Server is running on port 5000')
})
~~~

~~~ ruby
require 'sinatra'
require 'json'

set :port, 5000

before do
  @params = JSON.parse(request.body.read)
end

post '/' do
  content_type :json
  {
    replies: [{ type: 'text', content: 'Roger that' }],
    conversation: {
      memory: {
        key: 'value'
      }
    }
  }.to_json
end

post '/errors' do
  puts @params

  200
end
~~~

~~~ python
from flask import Flask, request, jsonify
import json

app = Flask(__name__)
port = '5000'

@app.route('/', methods=['POST'])
def index():
  print(json.loads(request.get_data()))
  return jsonify(
    status=200,
    replies=[{
      'type': 'text',
      'content': 'Roger that',
    }],
    conversation={
      'memory': { 'key': 'value' }
    }
  )

@app.route('/errors', methods=['POST'])
def errors():
  print(json.loads(request.get_data()))
  return jsonify(status=200)

app.run(port=port)
~~~

~~~ php
<?php
require 'vendor/autoload.php';
use \Slim\App;

$app = new App();

$app->post('/', function ($request, $response) {
  error_log($request->getBody()->getContents());
  return $response->withJson(array(
    'replies' => [
      array('type' => 'text', 'content' => 'Roger that')
    ],
    'conversation' => array(
      'memory' => array('key' => 'value')
    )
  ));
});

$app->post('/errors', function ($request, $response) {
  error_log($request->getBody()->getContents());
  return $response;
});

$app->run();
~~~
