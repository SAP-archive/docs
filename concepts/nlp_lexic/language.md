---
layout: concept
title: Language
permalink: /concepts/language
---

## Definition
We currently support all languages, with different levels of functionality: the **basic**, the **standard** and the **advanced** level.

<table class="mb3">
    <thead>
    <tr>
        <th width="25%"></th>
        <th>Basic</th>
        <th width="30%">Standard</th>
        <th>Advanced</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Languages</td>
        <td>All languages</td>
        <td><span class="flag-icon flag-icon-sa m1"></span><span class="flag-icon flag-icon-ct m1"></span><span
                class="flag-icon flag-icon-dk m1"></span><span class="flag-icon flag-icon-fi m1"></span><span
                class="flag-icon flag-icon-in m1"></span><span class="flag-icon flag-icon-it m1"></span><span
                class="flag-icon flag-icon-jp m1"></span><span class="flag-icon flag-icon-kr m1"></span><span
                class="flag-icon flag-icon-no m1"></span><span class="flag-icon flag-icon-nl m1"></span><span
                class="flag-icon flag-icon-pl m1"></span><span class="flag-icon flag-icon-pt m1"></span><span
                class="flag-icon flag-icon-ru m1"></span><span class="flag-icon flag-icon-se m1"></span><span
                class="flag-icon flag-icon-cn m1"></span></td>
        <td><span class="flag-icon flag-icon-gb m1"></span><span class="flag-icon flag-icon-fr m1"></span><span
                class="flag-icon flag-icon-es m1"></span><span class="flag-icon flag-icon-de m1"></span></td>
    </tr>
    <tr>
        <td>Intent Classification</td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Custom entities</td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Gold entities</td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Sentiment analysis</td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Enrichment, Type, Act</td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Language detection</td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    <tr>
        <td>Voice support</td>
        <td><i class="c-grey-400 ion-md-close"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
        <td><i class="c-blue-500 ion-md-checkmark-circle"></i></td>
    </tr>
    </tbody>
</table>

Bots are **multilingual**, which means you can speak several languages with the same bot.
To do that, add languages in each intent and create expressions in each of the tab. Recast.AI will **automatically** detect what the input language is so you can adapt your answers (only available for standard and advanced level languages).

After the language has been detected the following rules applies:
* If you do not have any expressions in this language, we will use your default bot language for processing.
* Else, we will use it for processing.

Follow [this tutorial](https://recast.ai/blog/build-multilingual-bot-hour/) to start building multilingual bot!

## Tips
* If you use a single language, pass your language as a request parameter to avoid the language detection step
* When you start constructing your intent in a new language, using a translation service can make the operation faster
* Don’t forget to set up all intents with the new language
* It could be useful for you to lock the user’s language after several exchanges, to avoid changing language when processing ambiguous international expressions like \`Ok\`,  \`Cool\` etc.

## Example
You have two intents in French and English, but none in Spanish, and your bot's default language is French.
* You receive an user utterance we detect as being Spanish:
We will use French as the processing language because your bot does not handle Spanish and return a JSON containing \`fr\` in the \`processing_language\` field, and \`es\` in the \`language\` field
* You send us an user utterance telling us it's English:
We will use English as the processing language and return a JSON containing \`en\` in the \`processing_language\` field, and \`en\` in the \`language\` field
* You receive an user utterance we detect as being French:
We will use French as the processing language and return a JSON containing \`fr\` in the \`processing_language\` field, and \`fr\` in the \`language\` field
* You send us an user utterance telling us it's Spanish:
We will use French as the processing language because your bot does not handle Spanish and return a JSON containing \`fr\` in the \`processing_language\` field, and \`es\` in the \`language\` field

