---
layout: concept
title: Webchat
permalink: /concepts/webchat
---

The Webchat Channel is developed by the Recast.AI team and is an open source project on Github.
You can use the default version of this webchat that we provide to you in the platform or customize it yourself by fork it and deploy it on your side.

## Default Hosted version

You need to activate this channel in the CONNECT tab of your bot.

### How to use it

1) Configure details like the color, the main title in the button, pictures etc..
2) just add this script into your page to get the webchat:

~~~ html
<script src="https://cdn.recast.ai/webchat/webchat.js"
channelId="CHANNEL_ID"
token="TOKEN_ID"
id="recast-webchat"
></script>
~~~

Note: `CHANNEL_ID` and `TOKEN_ID` can be found when creating a webchat channel in the bot connector.

## Open source version

- If you want to custom style or add new functionalities which does not exist in the default hosted version, you can fork the open source webchat.
- Link of Github webchat: <a href="https://github.com/Recastai/webchat" alt="Github Recast Webchat" target="_blank">Github RecastAI Webchat</a>

### How to use it
Please look at the `README.md`. It is developed in ReactJS.
