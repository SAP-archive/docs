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

    You can restrict messages from users to 512 characters or less. For example, you may want to do this if users tend to add a lot of details that obscure the intent of the request.
2) Add the following script to your page to get the webchat:

~~~ html
<script src="https://cdn.recast.ai/webchat/webchat.js"
channelId="CHANNEL_ID"
token="TOKEN_ID"
id="recast-webchat"
></script>
~~~

Note: You can find `CHANNEL_ID` and `TOKEN_ID` when creating a webchat channel in the Bot Connector.

## Open-source version

If you want to customize the style or add new functionalities that don't exist in the default hosted version, you can fork the open-source version on GitHub at <a href="https://github.com/Recastai/webchat" alt="Github Recast Webchat" target="_blank">RecastAI/Webchat</a>.

### How to use it
Please see the `README.md`. The open-source version is developed in ReactJS.
