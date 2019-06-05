---
layout: concept
title: Permissions at organization level
permalink: /concepts/permissions-at-organization-level
---

If you are the administrator of an organization, you can assign one of the following permissions as the base permission to all members of the organization. You can also assign one of the following permissions as an additional permission to a team of one or more members of the organization. You do this on the **Settings and Permissions** tab for the organization.
 
- No access  
  Members of the organization who have only this permission cannot see or access any of the organization's private bots. However, they can access its public bots.
  
- Read only  
  Members of the organization who have only this permission can access all of the organization's bots in read-only mode, that is, they can view, search, and filter all of the organization's bots. They can also fork any of the organization's bots, but only to a destination where they have read/write access.

- Read and write  
  Members of the organization who have only this permission can access all of the organization's bots in read/write mode, that is, they can edit, delete, transfer, and fork any of the organization's bots, as well as reload tokens.

- Create bot (+ Read and write)  
  Members of the organization who have this permission have the same access as members with **Read and write** permission, plus they can create new bots.

Administrators of an organization always have all rights, that is, they have **Create bot (+ Read and write)** permission, 
plus they can change the organization's settings, as well as manage teams and members.

## Base permission

The base permission is the default permission granted to all members of the organization and applied to all bots within the organization.

![SAP Conversational AI - Base permissions](https://cdn.cai.tools.sap/man/organisation/basepermissions.png)
 
For existing organizations, the default base permission is **Create bot (+ Read and write)**. For new organizations, the default base permission is **No access**.
 
## Team permissions

Team permissions let you give additional permissions to teams of one or more members of the organization. Team permissions are applied to all bots within the organization.

You create teams and add members to teams on the **Teams** tab. (Tip: You can also add members to teams on the **Members** tab.) You then assign the additional permission to the team on the **Settings and Permissions** tab. 

![SAP Conversational AI - Team permissions](https://cdn.cai.tools.sap/man/organisation/teampermissions.png)

Since these additional permissions are provided only to teams, if you want to assign an additional permission to only one member of the organization, you simply create a team with only that member.

When you create a new team, the default permission for the team is set to the base permission. The base permission is also the minimum credential that can be set for the team permission.

### Example

In your organization, the base permission is set to **No access**. You create two new teams: _Team 1_ and _Team 2_. Since the base permission is set to **No access**, the default permission for _Team 1_ and _Team 2_ is also set to **No access**.

Now, you change the team permission for _Team 2_ to **Read and write**. You then change the base permission to **Read only**. The team permission for _Team 1_ is updated accordingly to **Read only**.
