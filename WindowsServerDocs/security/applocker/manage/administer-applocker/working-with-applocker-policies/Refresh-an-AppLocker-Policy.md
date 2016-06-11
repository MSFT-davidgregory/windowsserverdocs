---
title: Refresh an AppLocker Policy
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4105cd7-786a-4d30-a3d7-d81663468f54
---
# Refresh an AppLocker Policy
This topic describes the steps to force an update for an AppLocker policy in  Windows Server 2012  and Windows 8.

If you update the rule collection on a local computer by using the Local Security Policy snap\-in, the policy will take effect immediately. If Group Policy is used to distribute the AppLocker policy and you want to immediately implement the policy, you must manually refresh the policy. The Group Policy refresh might take several minutes, depending upon the number of policies within the Group Policy Object \(GPO\) and the number of target computers.

To use Group Policy to distribute the AppLocker policy change, you need to retrieve the deployed AppLocker policy first. To prepare for the update and subsequent refresh, see [Edit an AppLocker Policy]() and [Use the AppLocker Windows PowerShell Cmdlets]().

To complete this procedure, you must have Edit Setting permission to edit a GPO. By default, members of the **Domain Admins** group, the **Enterprise Admins** group, and the **Group Policy Creator Owners** group have this permission.

#### To manually refresh the AppLocker policy by using Group Policy

1.  Open a Command Prompt window.

2.  At the command prompt, type **gpupdate \/force**, and then press ENTER.

3.  When the command finishes, close the Command Prompt window, and then verify that the intended rule behavior is correct. You can do this by checking the AppLocker event logs for events that include "policy applied."

To change a policy on an individual computer, or to implement that policy on other computers, without using Group Policy, you first need to update the rule within the rule collection. For information about updating existing rules, see [Edit AppLocker Rules](). For information about creating a new rule for an existing policy, see:

-   [Create a Rule That Uses a Publisher Condition]()

-   [Create a Rule That Uses a File Hash Condition]()

-   [Create a Rule That Uses a Path Condition]()

Membership in the local **Administrators** group, or equivalent, is the minimum required to complete this procedure.

**To refresh the AppLocker policy on the local computer**

-   Update the rule collection by using the Local Security Policy snap\-in with one of the following procedures:

    -   [Edit AppLocker Rules]()

    -   [Delete an AppLocker Rule]()

    -   [Configure Exceptions for an AppLocker Rule]()

When finished, the policy is in effect.

To make the same change on another computer, you can use any of the following methods:

-   From the computer that you made the change on, export the AppLocker policy, and then import the policy onto the other computer. To do this, use the AppLocker **Export Policy** and **Import Policy** features to copy the rules from the changed computer.

    > [!CAUTION]
    > When importing rules from another computer, all the rules will be applied, not just the one that was updated. Merging policies allows both existing and updated \(or new\) rules to be applied.

-   Merge AppLocker policies. For procedures to do this, see [Merge AppLocker Policies Manually](Merge-AppLocker-Policies-Manually.md) and [Merge AppLocker Policies by Using Set-ApplockerPolicy](Merge-AppLocker-Policies-by-Using-Set-ApplockerPolicy.md).

