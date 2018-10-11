---
layout: concept
title: Webchat
permalink: /concepts/webchat
---

The Webchat channel is developed by the Recast.AI team and is an open-source project on GitHub.
You can use the default version of the webchat that we provide in the platform or customize the open-source version by forking it and deploying it on your side.

## Default hosted version

On the **Connect** tab of your bot, activate the **Webchat** channel.

![Recast.AI - Webchat](//cdn.recast.ai/man/webchat-connector.png)

### How to use it

1) Configure details like color, title of the button, bot picture, user picture, etc.
2) Add the following script to your page to get the webchat:

~~~ html
<script src="https://cdn.recast.ai/webchat/webchat.js"
channelId="CHANNEL_ID"
token="TOKEN_ID"
id="recast-webchat"
></script>
~~~

Note: You can find `CHANNEL_ID` and `TOKEN_ID` when creating a webchat channel in the Bot Connector.

### Bot Memory management
One thing you might want to do is to send custom data from your website to the bot, like the name of the logged in user, his ID, the page he is currently on (to send product suggestions for example). To do that, you can define a `window.webchatMethods.getMemory` function, the webchat will call it before sending user messages, and send your arbitrary payload along with the message to the bot.

If you use Recast.AI's bot-builder (you should :)), your payload will be put in the memory of the conversation, meaning that you will be able to access this data in your bot-builder. Let's say you send this as payload : `{ "userName": "Dominik", "userId": 123456 }`, you will then be able to send this as a greeting message : `Hello {{ memory.userName }} ! How do you do ?`.

`window.webchatMethods.getMemory` must return a JSON object or a Promise resolving a JSON object :
  - `{ "memory": { ... }, "merge": <boolean> }`
where `{ ... }` is your arbitrary payload. `merge` is an instruction for the bot-builder. If set to true, the payload will be merged with the existing memory, overriding common keys but keeping the ones absent from the payload. If set to false, the memory will be replaced entirely by your payload.

If your `getMemory` function takes more than 10 seconds, the message will be sent anyway, without waiting for your function to finish.

#### Examples :
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
    <script src="https://cdn.recast.ai/webchat/webchat.js"
      channelId="<channelId>"
      token="<token>"
      id="recast-webchat"
    ></script>
  </body>
</html>
```

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

If you want to customize the style or add new functionalities that don't exist in the default hosted version, you can fork the open-source version on GitHub at <a href="https://github.com/Recastai/webchat" alt="Github Recast Webchat" target="_blank">RecastAI/Webchat</a>.

### How to use it
Please see the `README.md`. The open-source version is developed in ReactJS.
