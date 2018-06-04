---
layout: concept
title: Hello World
permalink: /concepts/hello-world
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

Each time a message is posted on one of the channels your bot is connected to, it receives a POST request on the endpoint you've set on the platform.
To reply, you need to make a post request with your bot's **Request Token** available in your bot settings.
In this example, we use SDKs to make it simpler. :)

## Receive messages and send "Hello world"

**1.** Copy-paste this snippet in a file.

**2.** Replace the **REQUEST_TOKEN** by your bot request token.

**3.** Install the dependencies by running the following command:

JS:
<span class="code">npm install recastai express body-parser</span>

Python:
<span class="code">pip install recastai flask</span>

Ruby:
<span class="code">gem install RecastAI sinatra</span>

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
var express = require('express')
var bodyParser = require('body-parser')
var recastai = require('recastai').default

var connect = new recastai.connect('YOUR_REQUEST_TOKEN')

var app = express()

/* Server setup */
app.set('port', 5000)
app.use(bodyParser.json())
app.post('/', function(req, res) {
  connect.handleMessage(req, res, onMessage)
})

function onMessage (message) {
  // Get the content of the message
  var content = message.content

  // Get the type of the message (text, picture,...)
  var type = message.type

  // Add a reply, and send it
  message.addReply([{ type: 'text', content: 'Hello, world' }])
  message.reply()
}

app.listen(app.get('port'), function () { console.log('App is listening on port ' + app.get('port')) })
~~~

~~~ ruby
require 'sinatra'
require 'recastai'

connect = RecastAI::Connect.new('YOUR_REQUEST_TOKEN')

set :port, 5000

post '/' do
  connect.handle_message(request) do |message|
    # Get the content of the message
    content = message.content

    # Get the type of the message (text, picture,...)
    type = message.type

    # Add a reply, and send it
    replies = [{type: 'text', content: 'Hello, world'}]

    connect.send_message(replies, message.conversation_id)
  end
end
~~~

~~~ python
from recastai import Connect
from flask import Flask, request, jsonify

connect = Connect('YOUR_REQUEST_TOKEN')

def bot(request):
  message = connect.parse_message(request)

  # Get the content of the message
  content = message.content

  # Get the type of the message (text, picture,...)
  type = message.type

  # Add a reply, and send it
  replies = [{type: 'text', content: 'Hello, world'}]

  connect.send_message(replies, message.conversation_id)

  return jsonify(status=200)

app = Flask(__name__)

@app.route('/', methods=['POST'])
def root():
  return bot(request)

app.run(port='5000')
~~~

~~~ php
<?php
use RecastAI\Client;

// Start Slim server
$app = new \Slim\App();

// Instantiate the Connect Client
$connect = Client::Connect($_ENV["YOUR_REQUEST_TOKEN"]);

//Handle / route
$app->post('/', function ($request, $response) {
  $connect->handleMessage($body, 'replyMessage');
});

function replyMessage ($message) {
  // Get the content of the message
  $text = $message->content;

  // Get the type of the message (text, picture,...)
  $type = $message->type;

  $message->addReply([(object)['type' => 'text', 'content' => 'Hello, world']]);

  $message->reply();
}

// Run Slim server
$app->run();
~~~
