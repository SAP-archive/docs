---
layout: concept
title: Training analytics
permalink: /concepts/training-analytics
---

In your bot page, in the **MONITOR** tab, you can find a *Training Analytics* section to help you build a great dataset. These analytics are only available for bots with more than 5 intents and more than 30 sentences by intents.

Your dataset (all your intents and entities that you created and trained) is a fundamental stone of your bot. If your bot is not well trained meaning your dataset is not well structured or not complete enough, it will not understand correctly a user input and the conversational experience will be desappointing.

## Your intent classification benchmark

At the top of the page, you can run a benchmark: It will trigger several processes to measure the performance of your dataset and give you insights on how to improve it.

A benchmark can be really long and take hours, depending on your bot size, you can have an idea here.

You can only have one benchmark running in the same time for your bot.

We use your bot training data and a validation file that you can provide to have more accurate results. Since we *take* your bot training data at a time **t**, and will provide tips and insights based on these data, we advise you to not update your dataset during the benchmark otherwise insights will be less accurate.


### Your bot training data

We split your expressions inside each of your intents in two parts: 90% is used for training, and 10% is used to evaluate the classification. The evaluation is simple: each sentence is tested with your training dataset and we check if the first intent returned is the right one. We repeat this process 5 times to enforce randomness in the splits. Once the evaluations are done, we average the results while taking in account the number of occurrences of each intent, resulting with 4 metrics between 0 and 1 for each intent: **Accuracy**, **Precision**, **Recall**, **F1 score**, and four global metrics on all the dataset.

Note that since we are evaluating by randomly picking 90% of your training dataset, on the same dataset, the scores can be a little bit different each time you run the benchmark.

### Your validation file

A validation file is composed of sentences with their corresponding intents. It reflects the reality, so it's important to build this file with real sentences that users had really said.

Each sentences will be tested with your training dataset and we check if the first intent returned is the right one. Once the evaluation is done, we also get 4 metrics between 0 and 1 on each intent and one global: **Accuracy**, **Precision**, **Recall**, **F1 score**.

### How can I create a validation file?

For multi-language bots, please upload one file per supported language.

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

The goal of this file is to represent reality - the way your users are using your bot. Real user entries should include dedicated vocabulary, typos etc. The proportions of presence of each intent in your file should also reflect the way real users are using your bot.

* Almost all of your bot intents should be represented (if a few intents, far from the core of you bot's usecase, are missing, that’s okay). At least 85% of the intents should be reprensented inside the validation file.
* Many sentences per intent should be present. Don’t choose some sentences over others.
* All sentences in your file should match an existing intent of your bot.
* Avoid duplicated sentences.

A recommended way to create your validation file while respecting the way people are using your bot would be:

1) Go to your Log feed page and filter only matched logs from the past 1 to 3 months.
2) Export these logs by clicking on "Merge duplicate logs on a single line".
3) Randomly pick the number of logs you need (rule of thumb: your bot intents count * 50).
4) Check manually (yes, you need to be the final validator), that each sentence is matching the right intent.
5) Create the final validation file with these sentences and intents.

In case you don't have at least 85% of your intents in your file, you need to pick again sentences from your logs to complete your file and reach approximately 85%. Here is how you can complete your file:

1) Go again in your Log feed page and search for specific intents that are missing.
2) Select between 3 and 10 sentences by missing intents and add these sentences to your validation file.

**Final step**
Upload your file to the platform, we'll analyse it and provide you a feedback - you may need to add some sentences. You will always be able to run a benchmark, these guidelines are just suggestions.

## Your benchmark scores

**Accuracy** is a global grade on the performance of your bot. It's the proportion of successful classifications out of all of the predictions conducted during your benchmark. While it's a good indication of performance for bots with balanced intents, it may be biased for unbalanced bots.

**Precision** is a metric that is calculated per intent. For each intent, it measures the proportion of correct predictions, out of all of the times the intent was declared during the benchmark. It answers the question *Out of all of the times my bot predicted this intent, how many times was it correct?*. Low precision usually signifies the relevant intent needs cleaning, meaning remove sentences that don't belongs to this intent.

For your bot users, a low precision means: *The bot always thinks I am talking about A, no matter what I say!*


**Recall** is also a metric calculated per intent. For each intent, it measures the proportion of correct predictions, out of all entries belonging to this intent. It answers the question *Out of all of the times my bot was supposed to detect this intent, how many times did it do so?*. Low recall usually signifies the relevant intent can use more training, by adding more sentences to enrich the training for example. 

For your bot users, a low recall means: *I cannot get the bot to understand I want to do B!*


**F1 score** is the harmonic mean of the precision and the recall. It's a good indication for the performance of each intent, ranging from 0 (bad performance) to 1 (good performance). The F1-scores for each intent can be averaged to create a global indication for the performance of your bot.

For your bot users, a low F1 score means: *This is completely useless*


## Your confusion Matrix

Your confusion matrix is used to gain further insight into intents that may clash and get confused. The element in the intersection of row A and column B signifies the percentage of sentences that should be classified as A but classified as B.

You can order the confusion matrix by intent name and by performance. If you don't have any problem between your intents you should have a confusion matrix with a beautifull diagonal, since 100% of expressions match the right intent, as expected.

![Recast.AI - Confusion Matrix](//cdn.recast.ai/man/monitoring/confusion-matrix.png)


## Tips to improve your intent classification

On top of benchmark metrics, we'll suggest actions on your dataset. We give you step by step suggestions to improve your dataset in a more accurate way. If suggestions are not meaningful for you, you can click on the button "Next tips".

Here is the list of suggestions that we can make, prioritized:

### Remove expressions
We can detect that a lot of testing examples of some intents are falsely predicted as another inent. Moreover we check if the number of training examples of this intent is more than 50% larger than the median number of examples in your dataset (it is said to be unbalanced). As a result, the algorithm may learn to increase the importance and detection rate of this intent. To prevent that, we advise removing any misclassified examples.

### Avoid duplicates
Machine learning algorithms are excellent at predicting the results of data that they encountered during the training step. Duplicates could end up in the training set and testing set, and anormally improve the benchmark results. 

### Add expressions
We check if some intents have a low **recall** (For each intent, it measures the proportion of correct predictions, out of all entries belonging to this intent.). Since there is no balance problem in your dataset, our ML strategy is unable to capture the globality of the semantic complexity of this intent. You may be able to solve this by adding more training examples. 

### Merge intents
Two intents may be too close semantically to be efficiently distinguished. A significant part of the error of one intent is directed toward the second one, and vice versa. Merging them may help improve the bot’s flow.

### Split intent
If an intent has both low precision and low recall, while the recall scores of the other intents are acceptable. It may reflect a use case that is too broad semantically, which would benefit from an intent-split into several intents. 



