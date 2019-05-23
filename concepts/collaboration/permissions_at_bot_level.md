---
layout: concept
title: Permissions at bot level
permalink: /concepts/permissions-at-bot-level
---

If you are the administrator of an organization, or if you have **Read and write** permission for the Settings module, you can assign one of the following permissions to a team for a given bot. You can assign the permission as a bot permission or as an environment permission (see below). You do this on the **Settings and Permissions** tab for the bot.

- Read only  
  The team can access the bot in read-only mode, that is, they can view, search, and filter the bot. They can also fork the bot, but only to a destination where they have read/write access.  
- Read and write  
  The team can access the bot in read/write mode, that is, they can edit, delete, and transfer the bot. They can also fork the bot, but only to a destination where they have read/write access.  

## Bot permissions
Bot permissions are granted to a specific team and applied to all versions of the bot, irrespective of the environment.
You can set these permissions individually for the following modules. For example, you can set **Read only** for the Train module, but **Read and write** for the Build module:

- Train  
  Includes the **Train** tab, NLP settings, log feed, and training analytics.  
- Build  
  Includes the **Build** tab and bot builder settings.  
- Connect  
  Includes the **Connect** tab and bot connector settings.  
- Settings  
  Includes the bot settings and permission management.  

(Screenshot)

By default, the bot permissions correspond to the permissions defined at organization level. See [Permissions at organization level](https://cai.tools.sap/docs/concepts/permissions-at-organization-level).

Note that the bot permissions correspond to the minimum environment permissions for a given team.

## Environment permissions

Environment permissions are granted to a specific team and applied to a particular environment (that is, the version of the bot that is linked to this environment) or to no environment (that is, all versions of the bot that are not linked to any environment). Examples of environments are Production, Development, and so on.

You can set these permissions individually for the following modules:

- Train  
  Includes the **Train** tab, NLP settings, log feed, and training analytics.  
- Build  
  Includes the **Build** tab and bot builder settings.  

(Screenshot)

By default, the environment permissions correspond to the permissions defined in the bot permissions. If no bot permissions are set, the permissions defined at organization level are applied.

