---
layout: concept
title: Webchat
permalink: /concepts/webchat
---

They are 2 versions of the webchat.

## Hosted version
Can be found here: <a href="https://cdn.recast.ai/webchat/webchat.js" alt="Webchat Script" target="_blank">CDN RecastAI Webchat script</a>
The hosted version webchat script is a compiled script of our webchat and has all functionalities supported by our platform.

### How to use it

Per default, you can just add this script into your page to get the webchat.

~~~ html
<script src="https://cdn.recast.ai/webchat/webchat.js"
channelId="CHANNEL_ID"
token="TOKEN_ID"
id="recast-webchat"
></script>
~~~

Note: `CHANNEL_ID` and `TOKEN_ID` can be found when creating a webchat channel in the bot connector.

## Open version

- If you want to custom style or add new functionalities which does not exist in the hosted version, you can fork the open source webchat.
- Link of Github webchat: <a href="https://github.com/Recastai/webchat" alt="Github Recast Webchat" target="_blank">Github RecastAI Webchat</a>

### How to use it
Please look at the `README.md`. It is developed in ReactJS.
