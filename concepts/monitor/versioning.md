---
layout: concept
title: Versioning
permalink: /concepts/versioning
---

You can use versions and environments to manage and update large, complex chatbots in an organized way that doesn't expose working drafts of a chatbot to users. 

## What's a version and why are they useful?

A version is a package of your bot training dataset and skills. Each version is independent of the others and can be managed individually. For example, you might want to create a new version prior to major updates to your training dataset or skills. Or you might want to create two or more variants of the same core bot for different audiences.  

## Enable versioning for your bot

**Note:** Once you enable versioning for your bot, you can't disable it.

To enable versioning for your bot:
1. Go to the **Settings** page for your bot.
2. Under **VERSION SETTINGS**, activate versioning.

At the top of the page, you'll now see a dropdown to create and switch to different versions.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-activation.png)

## How do I create a version?

By default, your bot has only one main version `v1`. You can create a new version under **VERSION SETTINGS** or in the dropdown near the bot name. Click **CREATE NEW VERSION** and select the version you want to copy. This copies the **Train** and **Build** tabs of the source version and creates a new version that you can then name. The new version is a pure copy; you can update the new version or the old one separately.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-new-version.png)

**Note:** Bots are restricted to eleven or fewer versions.

### Version request token

Each version has a dedicated request token. This means that if you want to analyze a text with the `/request` endpoint or use the Bot Builder API with the `/dialog` API, you have to provide the request token from the version that you want to use.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-tokens.png)

## What's an environment?

Environments are configurations applied to specific versions and help you to seamlessly deploy your chatbot in production. They are best leveraged as specific consumption environments, for example, Development, Staging, and Production.

When you first enable versioning, your first version `v1` is associated and linked to the environment `production`. You can create and name additional environments in the **VERSION SETTINGS** area under **Environments**.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versionings-envs.png)

Each environment is always linked to a specific version.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-env-version.png)

On the **Connect** tab, you can connect each channel to a specific environment. This means that you can have a Facebook Messenger channel for your `DEVELOPMENT` environment and link this environment to version `v2`, and have a Facebook Messenger channel for your `PRODUCTION` environment and link this environment to version `v1`. 

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-chanels.png)

### Environment request token

Each environment has a dedicated request token. This means that if you want to analyze a text with the `/request` endpoint or use the Bot Builder API with the `/dialog` API, you can either provide a `version token` or an `environment token`.

If you provide an `environment token` in your request, it uses the version of your chatbot that is linked to this environment.

## How do versions + environments work?

Since each environment is linked to a version, it's really easy to deploy a new version to a production environment.
Here you have two Facebook Messenger channels: one for the `DEVELOPMENT` environment and one for the `PRODUCTION` environment. The `v1` version of my bot is in the `PRODUCTION` environment. The users chatting with my Facebook Messenger page `Awesome bot` are chatting with this version.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-messenger.png)

Let's say I'm working on a different version `v2` and I'm testing it on the `DEVELOPMENT` environment with another Facebook Messenger page. I'm pretty comfortable with this new version and now I want to deploy it to the `PRODUCTION` environment.

On the **Settings** page for my bot, I go to **VERSION SETTINGS** and change the version that is linked to the `PRODUCTION` environment.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-deploy.png)

Now the `PRODUCTION` environment is linked to the `v2` version of my bot. The users on my Facebook Messenger page `Awesome bot` can now talk to the new version of my bot.

You can assign a version to multiple environments. However, you can assign only one version to each environment.


## How does the Bot Builder API (without Bot Connector) work?

If you're directly using the Bot Builder endpoint `/dialog` without a channel in the Bot Connector, the best practice is to use `environment` request tokens and not version tokens.

In your code, when you request SAP Conversational AI and send a message, it will always be on the same environment, for example, the `PRODUCTION` environment. When you need to deploy a new version of your chatbot to your users, you just need to go to the **Settings** page for your bot and, under **VERSION SETTINGS**, change the version that is linked to the `PRODUCTION` environment.

![SAP Conversational AI versioning](https://cdn.cai.tools.sap/man/monitoring/versioning-deploy.png)

You don't need to change the `request token` in your code because it's the same environment that you're requesting; you simply switch to a different version on the **Settings** page.


## Monitoring

On the **Monitor** tab, you can filter all of the metrics by environment and version. For example, you can opt to see only the log feed for the `STAGING` environment or only the usage metrics for the `PRODUCTION` environment.
