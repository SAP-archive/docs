---
layout: concept
title: Training analytics
permalink: /concepts/training-analytics
---

On the **Monitor** tab, the **Training Analytics** section helps you to build a great dataset for your bot. These analytics are only available for bots with at least 5 intents and at least 30 expressions per intent.

Your dataset (that is, all the intents and entities that you created and trained) is a fundamental element of your bot. If your bot isn't well-trained (meaning your dataset isn't well-structured or is incomplete), your bot won't be able to correctly understand messages from its users, resulting in a disappointing conversational experience.

## Your dataset benchmark

At the top of the page, you can run a benchmark. It will trigger several processes to measure the performance of your dataset and give you insights on how to improve your intent classification and your custom entity detection.

A benchmark can take several hours, depending on the size of your bot.

You can only run one benchmark at a time for your bot.

For more accurate results, we use your bot training data and a validation file that you provide. Since we take your bot training data at a time *t*, and provide tips and insights based on this data, we advise you not to update your dataset during the benchmark; otherwise the insights will be less accurate.

## Your intent classification benchmark

### Your bot training data

We split the expressions inside each intent into two parts: 90% is used for training, 10% is used to evaluate the classification. The evaluation is simple: Each sentence is tested with your training dataset, and we check if the first intent returned is the right one. We repeat this process five times to enforce randomness in the splits. Once the evaluation is done, we average the results while taking into account the number of occurrences of each intent. This results in three metrics between 0 and 1 for each intent (**Precision**, **Recall**, and **F1 score**) and three global metrics for the entire dataset.

Note that the scores may differ slightly if you run the benchmark again on the same dataset. This is because we randomly pick 90% of your training dataset to evaluate.

### Your validation file

A validation file is composed of sentences with their corresponding intents. It reflects the reality, so it's important to build this file with real sentences that users actually sent to your bot.

Each sentence is tested with your training dataset, and we check if the first intent returned is the right one. Once the evaluation is done, we also get three metrics between 0 and 1 for each intent (**Precision**, **Recall**, and **F1 score**) and one global metric.

### How do I create a validation file?

For multilingual bots, please upload one file for each supported language.

**File format**

Your file must be a valid CSV file. It must end with .csv and the separator must be a comma “,”. If you want to include quotes in your expressions or intents, you must add two double quotation marks before and after the quoted word(s).
For example, it should look like this:

~~~
"intent","expression"
"greetings","Hello"
"greetings","Hi"
"weather","What’s the weather in Paris?"
"translation","What does ""Bonjour"" in French mean?"
~~~

<br/>
**Content**

The goal of this file is to represent reality, that is, to show how users use your bot. Real user entries should include dedicated vocabulary, typos, etc. The proportion to which each intent is present in your file should also reflect the way real users use your bot. Here are some guidelines:

* Try to represent almost all intents in your bot. It's okay if a few intents, far from the core of your bot's use case, are missing. However, at least 85% of the intents should be represented in the validation file.
* Provide many sentences for each intent. Don’t choose some sentences over others.
* Check that all sentences in your file match an existing intent in your bot.
* Avoid duplicate sentences.

To ensure that your validation file reflects the way that people actually use your bot, we recommend creating your file as follows:

1) On the **Monitor** tab, go to **Log Feed** and filter matched **and** unmatched production logs from the past 1 to 3 months.

2) Export these logs by clicking **Merge duplicate logs on a single line**.

3) Randomly pick the number of logs you need (as a rule of thumb, your bot intent count * 50).

4) Check manually (yes, you need to be the final validator!) that each sentence matches the right intent.

5) Create the final validation file with these sentences and intents.

If your file doesn't include at least 85% of your intents, you need to pick sentences from your logs to complete your file and reach approximately 85%. You can do this as follows:

1) Go back to your **Log Feed** page and search for the specific intents that are missing.

2) Select between 3 and 10 sentences for each missing intent, and add these sentences to your validation file.

**Final step**
Upload your file to the platform. We'll analyze it and provide feedback. For example, we may suggest adding more sentences. You can still run a benchmark at any time; these guidelines are just suggestions.

## Your benchmark scores

**Precision** is a metric that is calculated per intent. For each intent, it measures the proportion of correct predictions out of all the times the intent was declared during the benchmark. It answers the question *Out of all the times my bot predicted this intent, how many times was it correct?* Low precision usually signifies the relevant intent needs cleaning, which means removing sentences that don't belong to this intent.

For your bot users, a low precision means *The bot always thinks I'm talking about A, no matter what I say!*

**Recall** is also a metric calculated per intent. For each intent, it measures the proportion of correct predictions out of all the entries belonging to this intent. It answers the question *Out of all the times my bot was supposed to detect this intent, how many times did it do so?* Low recall usually signifies the relevant intent needs more training, for example, by adding more sentences to enrich the training.

For your bot users, a low recall means *I can't get the bot to understand that I want to do B!*

**F1 score** is the harmonic mean of the precision and the recall. It's a good indication for the performance of each intent, ranging from 0 (bad performance) to 1 (good performance). The F1 scores for each intent can be averaged to create a global indication for the performance of your bot.

For your bot users, a low F1 score means *This is completely useless!*


## Your intent confusion matrix

Your confusion matrix is used to gain further insight into intents that may clash and get confused. The element at the intersection of row A and column B signifies the percentage of sentences that should be classified as A, but are classified as B.

You can order the confusion matrix by intent name and by performance. If you don't have any problems between your intents, you should have a confusion matrix with a beautiful diagonal since 100% of expressions match the right intent, as expected.

![SAP Conversational AI - Confusion Matrix](//cdn.cai.tools.sap/man/monitoring/confusion-matrix.png)


## Tips to improve your intent classification

In addition to benchmark metrics, we provide step-by-step suggestions to improve your dataset in a more accurate way. If the suggestions are not meaningful for you, click **Next tips**.

Here's a prioritized list of the suggestions we may make.

### Remove expressions
We can detect that a lot of testing examples of some intents are falsely predicted as another intent. Moreover, we check if the number of training examples of this intent is more than 50% larger than the median number of examples in your dataset (it is said to be unbalanced). As a result, the algorithm may learn to increase the importance and detection rate of this intent. To prevent that, we advise removing any misclassified examples.

### Avoid duplicates
Machine learning algorithms are excellent at predicting the results of data that they encountered during the training step. Duplicates could end up in the training set and testing set, and abnormally improve the benchmark results.

### Add expressions
We check if some intents have a low **recall** (see definition above). Since there is no balance problem in your dataset, our machine learning strategy is unable to capture the globality of the semantic complexity of this intent. You may be able to solve this by adding more training examples.

### Merge intents
Two intents may be too close semantically to be efficiently distinguished. A significant part of the error of one intent is directed toward the second one, and vice versa. Merging them may help improve the bot’s flow.

### Split intent
If an intent has both low precision and low recall, while the recall scores of the other intents are acceptable, it may reflect a use case that is too broad semantically. Try splitting this intent into several intents.

## Reality check

This helps you to ensure that your dataset represents reality as far as possible.

Before you can carry out a reality check, you must first upload a validation file (see *How do I create a validation file?* above).

Under **Make your dataset closer to reality**, choose an intent in the dropdown. You’ll then get metrics about how close your training dataset is to reality (from your validation file), as well as suggestions to improve your dataset. For example, you can find the length of the expressions in your training dataset compared with the medium length of the sentences sent by your users. You can also find the most important words in your intent compared with the most important words when your users chat. If some words are missing in your dataset, or if some words are never used by your users, we provide tips to help you solve the issue.

## Your entity detection benchmark

We split the expressions inside each intent into two parts: 90% is used for training, 10% is used to evaluate the custom entity detection. The evaluation is simple: We detect each custom entity in each sentence, based on the knowledge we have from the training dataset. We check if each word has been properly detected as a custom entity or as a simple word. We repeat this process five times to enforce randomness in the splits. This results in five metrics between 0 and 1 for each entity (**Precision**, **Recall**, **F1 score**, **Ranking**, and **Size**) and five global metrics for the entire dataset.

## Your entity detection confusion matrix

Your confusion matrix is used to gain further insight into entities that may clash and get confused. The element at the intersection of row A and column B signifies the percentage of entities that should be detected as A, but are detected as B.

## Tips to improve your entity detection

### Remove values
Too many words are tagged as custom entities in your chatbot. Custom entities should be used and tagged on words only if you really need them to detect and retrieve key information from your users.

### Add different values
You’re using the same value too many times in this entity. This can be intentional if you want to check that something is present or not (and you don’t need to detect several values). If this is the case, please ignore this tip. If not, you may want to either delete this entity because you’re not really using it, or add different values.

### Remove mistagging errors
A custom entity is always confused with another one. You may have a tagging issue. For example, some values may be tagged in both entities, or an entity is mistagged. If it’s not a mistagging issue, the entities may be too similar; check whether you can merge them.
