---
layout: concept
title: Hello World
permalink: /concepts/hello-world
---

Each time a message is posted on one of the channels your bot is connected to, it receives a POST request on the endpoint you've set on the platform.
To reply, you need to make a post request with your bot's **Request Token** available in your bot settings.
In this example, we use SDKs to make it simpler. :)

## Receive messages and send "Hello world"

**1.** Copy-paste this snippet in a file.

**2.** Replace the **REQUEST_TOKEN** by your token.

**3.** Install the dependencies and run the file




JS: \`npm install recastai express body-parser\`

Python: \`pip install recastai flask\`

Ruby: \`gem install RecastAI sinatra\`

PHP: \`composer require recastai/sdk-php\`

**TODO** get the code snippet

