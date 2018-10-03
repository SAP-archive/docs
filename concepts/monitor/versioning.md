---
layout: concept
title: Versioning
permalink: /concepts/versioning
---

Versions and Environments may be used to manage and update large, complex chatbots in an organized way that does not expose working drafts of a chatbot to chatbot consumers. 

## Enable bot versioning

By default, your bot has only one main version `v1`. To enable versioning feature, go to the Settings, in the Versions Settings area and activate the feature. Once this feature is enabled, it may not be disabled.

You will then see at the top of your page a drop-down to create and switch to different versions.

[IMAGE]

## What's a Version?

A version is a package of your bot training dataset and your skills. Each version is independent of other one and can be managed individually. 

A new version can be created within the Version Settings area or in the drop-down near your bot name. Click the 'Create New Version' button and select the Version which to copy. This copies the Build and Train tabs of the source Version and creates a new Version which can then be named. The new Version is a pure copy, it means that you can update the new one or the old one separatly.

[IMAGE]

It is best to create a new Version prior to major updates to your skills or your training dataset. Additionally, separate versions may be useful when you want to leverage two variations of the same core bot. 

**Note: Bots are restricted to having five or fewer Versions.**

### Version request token

Each version has a dedicated request token. It means that if you want to analyse a text with the `/request` endpoint or use the Bot Builder API with the `/dialog` API, you will now have to provide the request token from the version you want to use.

[IMAGE]

## What's an Environment?

Environments are configurations applied to specific versions and will help you to deploy seamlessly your chatbot in production. They are best leveraged as specific consumption environments, for example: Development, Staging, and Production.

When you first enable the versioning feature, your first version `v1` will be associated and linked to the environment `production`. Additional Environments may be created and named within the Environments area in Versions Settings.

[IMAGE]

Each environment is always linked to a specific version.

[IMAGE]

In the **CONNECT** tab you will be able to connect each channel to a specific environment. It means that you can have a Facebook Messenger channel for your `DEVELOPMENT` environment, and this environment is linked to the version `v2`, and you can have a Facebook Messenger channel for your `PRODUCTION` environment, and this environment is linked to the version `v1`. 

[IMAGE]

### Environment request token

Each environment has a dedicated request token. It means that if you want to analyse a text with the `/request` endpoint or use the Bot Builder API with the `/dialog` API, you can either provide a `version token` or an `environment token`.

If you provide an `environment token` in your request, it will use the version of your chatbot linked to this environment.

## Versions + Environments: How Does it Work?

Since each environment is linked to a version, it's really easy to deploy a new version to a production environment.
Here you have to Facebook Messenger channels, one for the `DEVELOPMENT` and for the `PRODUCTION`. Now, the `v1` version of my bot is in `PRODUCTION`, and users that are chatting with my facebook page `Awesome bot` are chatting with this one.

[IMAGE]

Let's say that I'm working on a different version `v2`, and I'm testing it on a `STAGING` environement, so with another Facebook Messenger page. I'm pretty confortable with this new version, and now I want to deploy it to the `PRODUCTION` environment.

I go to the settings, on the versions area, and change the version that is linked to the `PRODUCTION`.

[IMAGE]

Now the `PRODUCTION` environment is linkes to my `v2` version of my bot, and my users on my Facebook Messenger page `Awesome bot` can talk to the new version of my bot.

Each Versions may be assigned to multiple Environments, however only a single Version can be assigned to each Environment.


## Bot Builder API (without Bot Connector): how it work?

If you are using directly the Bot Builder endpoint `/dialog` without a channel in Bot Connector. The best practice is to use `environment` request tokens and not versions tokens.

In your code, when you will request Recast.AI and send a message, it will be always on the same environment, the `PRODUCTION` one for example. When you will need to deploy a new version of your chatbot to your users, you will just need to go to the settings, in the versions area, and change the version that is linked to the `PRODUCTION` environment.

[IMAGE]

You will not need to change the `request token` in your code, since it's the same environment that you are requesting, and it's in the Recast.AI settings that you will switch to a different version.


## Monitoring

In all areas of the Monitor tab, the metrics shown can be filtered on a specific environment and versions. For example, you can opt to only see the Log Feed generated on a `STAGING` environment or see the Usage Metrics only on the `PRODUCTION` environment.
