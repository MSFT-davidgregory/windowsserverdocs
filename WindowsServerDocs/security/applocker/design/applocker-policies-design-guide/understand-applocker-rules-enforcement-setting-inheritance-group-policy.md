---
title: Understand applocker Rules and Enforcement Setting Inheritance in Group Policy
ms.custom: na
ms.prod: windows-server-2012-r2
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba9ab7f0-ca9c-46fc-8de0-fdf188e0fa55
---
# Understand applocker Rules and Enforcement Setting Inheritance in Group Policy
This topic for the IT professional describes how application control policies configured in applocker are applied through Group Policy.

Rule enforcement is applied only to collections of rules, not individual rules. applocker divides the rules into the following collections: executable files, Windows Installer files, scripts, Packaged apps and Packaged app installers, and DLL files. The options for rule enforcement are **Not configured**, **Enforce rules**, or **Audit only**. Together, all applocker rule collections compose the application control policy, or applocker policy.

Group Policy merges applocker policy in two ways:

-   **Rules.** Group Policy does not overwrite or replace rules that are already present in a linked Group Policy Object \(GPO\). For example, if the current GPO has 12 rules and a linked GPO has 50 rules, 62 rules are applied to all computers that receive the applocker policy.

    > [!IMPORTANT]
    > When determining whether a file is permitted to run, applocker processes rules in the following order:
    > 
    > 1.  **Explicit deny.** An administrator created a rule to deny a file.
    > 2.  **Explicit allow.** An administrator created a rule to allow a file.
    > 3.  **Implicit deny.** This is also called the default deny because all files that are not affected by an allow rule are automatically blocked.

-   **Enforcement settings.** The last write to the policy is applied. For example, if a higher\-level GPO has the enforcement setting configured to **Enforce rules** and the closest GPO has the setting configured to **Audit only**, **Audit only** is enforced. If enforcement is not configured on the closest GPO, the setting from the closest linked GPO will be enforced.

Because a computer's effective policy includes rules from each linked GPO, duplicate rules or conflicting rules could be enforced on a user's computer. Therefore, you should carefully plan your deployment to ensure that only rules that are necessary are present in a GPO.

The following figure demonstrates how applocker rule enforcement is applied through linked GPOs.

![](../../../media/understand-applocker-rules-enforcement-setting-inheritance-group-policy/applocker-plan-inheritance.gif)

In the preceding illustration, note that all GPOs linked to Contoso are applied in order as configured. The rules that are not configured are also applied. For example, the result of the Contoso and Human Resources GPOs is 33 rules enforced, as shown in the client HR\-Term1. The Human Resources GPO contains 10 non\-configured rules. When the rule collection is configured for **Audit only**, no rules are enforced.

When constructing the Group Policy architecture for applying applocker policies, it is important to remember:

-   Rule collections that are not configured will be enforced.

-   Group Policy does not overwrite or replace rules that are already present in a linked GPO.

-   applocker processes the explicit deny rule configuration before the allow rule configuration.

-   For rule enforcement, the last write to the GPO is applied.

