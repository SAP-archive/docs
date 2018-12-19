---
layout: concept
title: Webchat
permalink: /concepts/webchat
---

The Webchat channel is developed by the SAP Conversational AI team and is an open-source project on GitHub.
You can use the default version of the webchat that we provide in the platform or customize the open-source version by forking it and deploying it on your side.

## Default hosted version

On the **Connect** tab of your bot, activate the **Webchat** channel.

![SAP Conversational AI - Webchat](//cdn.cai.tools.sap/man/webchat-connector.png)

### How to use it

1) Configure details like color, title of the button, bot picture, user picture, etc. If you wish, you can restrict messages from users to 512 characters or less. For example, you may want to do this if users tend to add a lot of details that obscure the intent of the request.

2) Add the following script to your page to get the webchat:

~~~ html
<script src="https://cdn.cai.tools.sap/webchat/webchat.js"
channelId="CHANNEL_ID"
token="TOKEN_ID"
id="recast-webchat"
></script>
~~~

Note: You can find `CHANNEL_ID` and `TOKEN_ID` when creating a webchat channel in the Bot Connector.

### Bot memory management
You might want to send custom data from your website to the bot, like the name of the logged in user, their ID, and the page they are currently viewing (for example, to send product suggestions). To do that, you can define a `window.webchatMethods.getMemory` function. The webchat will call this function before sending user messages. It will then send your arbitrary payload along with the message to the bot.

If you use the Bot Builder (which we highly recommend!), your payload is put in the conversation memory. This enables you to access this data in the Bot Builder. Let's say you send this as the payload: `{ "userName": "Dominik", "userId": 123456 }`. You can then send this as a greeting message: `Hello {{ memory.userName }}! How do you do?`

`window.webchatMethods.getMemory` is called with the parameter `conversationId` and must return a JSON object or a promise resolving a JSON object:

```javascript
{
  "memory": { "userName": "Dominik" },
  "merge": true
}
```


| Key                   | Required | Value
|-----------------------|----------|-------------------------------------------|
| memory               | Required | An object like { "userName": "Dominik" }   |
| merge          | Optional | A boolean: If set to true, the payload is merged with the existing memory, overriding common keys, but keeping the ones absent from the payload. If set to false or missing, the memory is replaced entirely by your payload. |


If your `getMemory` function takes more than 10 seconds, the message is sent anyway, without waiting for your function to finish.

#### Examples :

Here's a simple example:
```html
<html>
  <head>
    <script>
      window.webchatMethods = {
        // called at each user message
        getMemory: (conversationId) => {
          const memory = { userName: 'Dominik Bousquet', userId: 123456 }
          return { memory, merge: true }
        }
      }
    </script>
  </head>
  <body>
    <script src="https://cdn.cai.tools.sap/webchat/webchat.js"
      channelId="<channelId>"
      token="<token>"
      id="recast-webchat"
    ></script>
  </body>
</html>
```

Here's an example to retrieve the user information from the cookie and page URL:

```javascript
window.webchatMethods = {
  getMemory: (conversationId) => {
    const getCookie = (name) => {
      const value = document.cookie.match('(^|;) ?' + name + '=([^;]*)(;|$)')
      return value ? value[2] : null
    }
    const userName = getCookie('userName')
    const memory = { userName, currentUrl: window.location.href }
    return { memory, merge: true }
  }
}
```

Here's an example to retrieve the user information from an API call:

```javascript
window.webchatData = {}
window.webchatMethods = {
  getMemory: (conversationId) => {
    if (window.webchatData.savedUserData) {
      return { memory: window.webchatData.savedUserData, merge: true }
    }
    return new Promise((resolve, reject) => {
      axios.get('/current_user')
        .then((response) => {
          const memory = { userName: response.data.name, userId: response.data.id }
          window.webchatData.savedUserData = memory
          resolve({ memory, merge: true })
        })
        .catch(reject)
    })
  }
}
```

Finally, here's an example with the page URL information and reset memory information:

```javascript
window.webchatData = {}
window.webchatMethods = {
  getMemory: (conversationId) => {
    if (!window.webchatData.oriUrl) {
      window.webchatData.oriUrl = window.location.href
    }
    // merge: false - reset the conversation if the user
    // switched to another page since the first message
    if (window.webchatData.oriUrl !== window.location.href) {
      return { memory: {}, merge: false }
    }
    return { memory: { userName: 'Dominik' }, merge: true }
  }
}
```


## Open-source version

If you want to customize the style or add new functionalities that don't exist in the default hosted version, you can fork the open-source version on GitHub at <a href="https://github.com/SAPConversationalAI/webchat" alt="GitHub SAP Conversational AI Webchat" target="_blank">SAPConversationalAI/Webchat</a>.

### How to use it
Please see the `README.md`. The open-source version is developed in ReactJS.
