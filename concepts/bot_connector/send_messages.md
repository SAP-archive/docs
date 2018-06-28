---
layout: concept
title: Send rich messages
permalink: /concepts/structured-messages
---


To send a message, you need to make a post request with your bot's **Request Token** available in your bot settings and send specific payload for each message type.

<div class="mt2" />

## Message format

In the following payloads, buttons can either be:

* **postback**: the basic type, once the button is tapped, the value is sent as a normal incoming message
* **web_url**: depending on the channel, once this button is tapped, the URL in the value field is loaded
* **phone_number**: depending on the channel, once this button is tapped, the phone number in the value field will be called

<div class="mt2" />

### Text Message

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-text.svg"
    class="custom mb2 mr4"
    alt="Bot Connector - messenger text format"
  />
  <div class="flex-grow" markdown="1">

  ~~~ json
    {
      "type": "text",
      "content": "MY_TEXT",
    }
  ~~~

  </div>
</div>

### Quick Replies

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-quickreplies.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - messenger Quick Replies format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "quickReplies",
    "content": {
      "title": "TITLE",
      "buttons": [
        {
          "title": "BUTTON_TITLE",
          "value": "BUTTON_VALUE"
        }
      ]
    }
  }
  ~~~

  </div>
</div>

### Cards

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-cards.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger Card format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "card",
    "content": {
      "title": "CARD_TITLE",
      "subtitle": "CARD_SUBTITLE",
      "imageUrl": "IMAGE_URL",
      "buttons": [
        {
          "title": "BUTTON_TITLE",
          "type": "BUTTON_TYPE",
          "value": "BUTTON_VALUE"
        }
      ]
    }
  }
  ~~~

  </div>
</div>

### Buttons

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-buttons.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger Buttons format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "buttons",
    "content": {
      "title": "BUTTON_TITLE",
      "buttons": [
        {
          "title": "BUTTON_TITLE",
          "type": "BUTTON_TYPE",
          "value": "BUTTON_VALUE"
        }
      ]
    }
  }
  ~~~

  </div>
</div>

### Carousel

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-carousel-01.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger Carousel format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "carousel",
    "content": [
      {
        "title": "CARD_1_TITLE",
        "subtitle": "CARD_1_SUBTITLE",
        "imageUrl": "IMAGE_URL",
        "buttons": [
          {
            "title": "BUTTON_1_TITLE",
            "type": "BUTTON_1_TYPE",
            "value": "BUTTON_1_VALUE"
          }
        ]
      }
    ]
  }
  ~~~

  </div>
</div>

### List

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-list.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger List format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "list",
    "content": {
      "elements": [
        {
          "title": "ELEM_1_TITLE",
          "imageUrl": "IMAGE_URL",
          "subtitle": "ELEM_1_SUBTITLE",
          "buttons": [
            {
              "title": "BUTTON_1_TITLE",
              "type": "BUTTON_TYPE",
              "value": "BUTTON_1_VALUE"
            }
          ]
        }
      ],
      "buttons": [
        {
          "title": "BUTTON_1_TITLE",
          "type": "BUTTON_TYPE",
          "value": "BUTTON_1_VALUE"
        }
      ]
    }
  }
  ~~~

  </div>
</div>

### Picture

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-image.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger Picture format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "picture",
    "content": "IMAGE_URL",
  }
  ~~~

  </div>
</div>

### Video

<div class="flex flex-center mb3">
  <img
    src="https://cdn.recast.ai/website/bot-connector/recast-ai-bc-video.svg"
    class="custom m0 mb2 mr4"
    alt="Bot Connector - Messenger Video format"
  />

  <div class="flex-grow" markdown="1">

  ~~~ json
  {
    "type": "video",
    "content": "VIDEO_URL",
  }
  ~~~

  </div>
</div>

## Send the message

### Sending a message to a conversation

<span class='label label-post'>POST</span> `https://api.recast.ai/connect/v1/conversations/:conversation_id/messages`

| Name | Type | Description | Constraints |
| -----| ---- | ----------- | -------- |
| `messages` | `Array[Object]` | The messages you want to send | Required  |


### Broadcast a message to all your bot's conversations

<span class='label label-post'>POST</span> `https://api.recast.ai/connect/v1/messages`

| Name | Type | Description | Constraints |
| -----| ---- | ----------- | -------- |
| `messages` | `Array[Object]` | The messages you want to send | Required |

## Response

If your call is successful, you should receive a 201.


#### Errors

We return an error (`400: bad_request`) if any of these cases is met:

* Parameter `messages` is missing.

We return an error (`401: unauthorized`) if the following case is met:

* The token provided in your request is not linked to any of your bots.

We return an error (`503: service_unavailable`) if any of these cases is met:

* The service you interact with (Messenger, Kik, Slack,...) is unavailable.

