---
layout: concept
title: Permissions at bot level
permalink: /concepts/permissions-at-bot-level
---


If you are the administrator of an organization or if you have Read and Write permissions on “Settings”, you can assign one of the following permissions as the base permission to all members of the organization. You can also assign one of the following permissions as an additional permission to a team of one or more members of the organization. You do this on the bot Settings and Permissions tab.  
- Read only  
  The team has access in read-only mode, that is, it can view, search, and filter. The team can also fork, but only to a destination where it has read/write access.
- Read and write  
  The team has access in read/write mode, that is, it can edit, delete, transfer. The team can also fork, but only to a destination where it has read/write access.

## Bot permission
The bot permission is granted to a specific team and applied to all versions of this bot, irrespective of the environment.
You can define bot permission on the following list of modules :
- Train  
  Includes the Train tab, NLP settings, log feed, and training analytics  
- Build  
  Includes the Build tab and bot builder settings  
- Connect  
  Includes the Connect tab and bot connector settings  
- Settings  
  Includes the bot settings and permission management  

(Screenshot)

By default, the bot permission corresponds to the permissions defined at organization level. (link: https://cai.tools.sap/docs/concepts/permissions-at-organization-level )

Note that the bot permissions correspond to the minimum environment permissions for a given team.

## Specific permissions

The specific permissions are granted to a specific team and applied to a particular environment (that is, the version of the bot that is linked to this environment) or to no environment (that is, all versions of the bot that are not linked to any environment)

You can define specific permissions on the following list of modules:

- Train  
  Includes the Train tab, NLP settings, log feed, and training analytics  
- Build  
  Includes the Build tab and bot builder settings  

(Screenshot)

By default, the specific permission corresponds to the permissions defined in the bot permission. If nothing is set, the organization level permissions are applied.

