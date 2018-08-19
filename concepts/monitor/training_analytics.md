---
layout: concept
title: Training analytics
permalink: /concepts/training-analytics
---

## How can I create a validation file?

A validation file is composed of sentences with the corresponding intent.
You have to upload one file per language. It means that you will only have sentences from the same language in the same file.

**About the file format:**

Your file should be a valid CSV file. It should end with .csv and the separator should be a comma “,”.
It should look like this:

~~~ json
“expressions”,”intents”
“Hello”,”greetings”
“Hi”,”greetings”
“What’s the weather in Paris”,”weather”
~~~

**About the content**

The goal of this file is to represent the reality, the way your users are currently speaking (with a dedicated vocabukary, with some typos etc..) but also the topics or intents they are more speaking about.

* All your bot intents should be represented (almost all - if few intents, far from the heart of your bot main usecase, are missing it’s okay). More or less 85% of the intents must be reprensented inside the validation file.
* Many sentences per intents should be present. Don’t choose some sentences over other.
* All sentences in your file should match an existing intent of your bot.
* Avoid duplicate sentences.

Here is a way to fill this file by respecting the way people are using your bot:

1) Go in your Log feed page, and filter only matched logs from the past 1 to 3 months.
2) Export these logs by clicking on "Merge duplicate logs on a single line".
3) Randomly pick the number of logs you need (to calculate this number: your bot intents count * 50).
4) Check manually (yes, you need to be the final validator), that each sentence is matching the right intent.
5) Create the final validation file with these sentences and intents.

**Final step**
Upload your file in the platform, we'll analyse it and provide you a feedback. Maybe you'll need to add some sentences. You will always be able to run a benchmark, all of these guidelines are just suggestions.
