---
layout: concept
title: Code and webhook
permalink: /concepts/code-and-webhook
---


If you want to extend Bot Builder with custom code, you can call your API with webhook actions.

![Recast.AI - Webhook url](//cdn.recast.ai/man/recast-ai-webhook-view.png)

You must provide a full url or route (starting with a '/') to be called by Bot Builder, allowing you to run code or API calls.

If you provide a route, it will be added to your bot's base url (configurable in your bot's settings).

![Recast.AI - Bot url settings](//cdn.recast.ai/man/recast-ai-settings-bot-url.png)

Since the current version of webhook does not support authentication headers, your endpoints are open and reachable from anywhere.
We have version 2.0 in the works which will let you secure all external endpoints.

## What your code will receive

You will receive a POST HTTP request on this route, with all the conversation state.

Then you can perform any calculation, database checks or external API calls and send back data to Bot Builder.
The body format is the following:

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

## How to format your reply?

Send back a formatted message, Bot Builder will forward it to the user.
Of course all messages format from Bot Connector are supported.

## Code example

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
