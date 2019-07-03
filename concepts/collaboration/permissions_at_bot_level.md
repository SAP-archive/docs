---
layout: concept
title: Permissions at bot level
permalink: /concepts/permissions-at-bot-level
---

If you are the administrator of an organization, or if you have **Read and write** permission for the Settings module, you can assign one of the following permissions to a team for a given bot. You can assign the permission as a bot permission or as an environment permission (see below). You do this on the **Settings and Permissions** tab for the bot.

- Read only  
  The team can access the bot or module in read-only mode, that is, they can view, search, and filter the bot items. They can also fork the bot, intents, entities or skills, but only to a destination where they have read/write access.  
- Read and write  
  The team can access the bot or module in read/write mode, that is, they can edit, delete the bot or bot items and transfer the bot. They can also fork the bot, intents, entities or skills as well as reload tokens, but only to a destination where they have read/write access.  

<br />
![SAP Conversational AI organization_permissions](https://cdn.cai.tools.sap/man/organisation/Permissions.png)

**Notes:**
- Request tokens for at least one module of the bot are displayed to the team with Read Only access, but it can be reloaded only if you are the administrator of an organization or if you have Read and Write permissions on **Settings**.
- Dev tokens are displayed and can be reloaded only if you are the administrator of an organization or if you have Read and Write permissions on **Settings**.
 
## Bot permissions
Bot permissions are granted to a specific team and applied to all versions of the bot, irrespective of the environment.

You can set these permissions individually for the following modules. For example, you can set **Read only** for the Train module, but **Read and write** for the Connect module:

- Train  
  Includes the **Train** tab, NLP settings, log feed, and training analytics.  
- Build  
  Includes the **Build** tab and bot builder settings.  
- Connect  
  Includes the **Connect** tab and bot connector settings.  
- Settings  
  Includes the bot settings and permission management.
 
<br />
 
![SAP Conversational AI bot_choose_team](https://cdn.cai.tools.sap/man/organisation/Bot-Chooseteam.png)

![SAP Conversational AI bot_set_permissions](https://cdn.cai.tools.sap/man/organisation/Bot-set-permissions.png)

**Notes:**
- Permissions that you apply to **Build** are also replicated to **Train**.
- Permissions that you apply to **Settings** are also replicated to **Train** and **Build**.  
 
<br />
 
By default, the bot permissions correspond to the permissions defined at organization level. See [Permissions at organization level](https://cai.tools.sap/docs/concepts/permissions-at-organization-level).

Note that the bot permissions correspond to the minimum environment permissions for a given team.

## Environment permissions

Environment permissions are granted to a specific team and applied to a particular environment (that is, the version of the bot that is linked to this environment) or to no environment (that is, all versions of the bot that are not linked to any environment). Examples of environments are Production, Development, and so on.

You can set these permissions individually for the following modules:

- Train  
  Includes the **Train** tab, NLP settings, log feed, and training analytics.  
- Build  
  Includes the **Build** tab and bot builder settings.  
  
<br />

![SAP Conversational AI environment_choose_env](https://cdn.cai.tools.sap/man/organisation/Env-Choose-env.png)

![SAP Conversational AI environment_set_permissions](https://cdn.cai.tools.sap/man/organisation/Env-set-permissions.png)

**Note:** Permissions that you apply to **Build** are also replicated to **Train**.

By default, the environment permissions correspond to the permissions defined in the bot permissions. If no bot permissions are set, the permissions defined at organization level are applied.

