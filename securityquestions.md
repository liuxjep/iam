---

copyright:

  years: 2018, 2020

lastupdated: "2020-04-16"

keywords: security questions, MFA, multifactor authentication, login security

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Enabling MFA security questions for a user
{: #questions}

As an administrator with the correct access, you can enable the option for a user to be prompted for security questions and answers at login. This type of multifactor authentication (MFA) is required only for the account where the setting is enabled. This type of multifactor authentication (MFA) is required only for the account where the setting is enabled unlike ID-based MFA. For more information, see [Types of multifactor authentication](/docs/iam?topic=iam-types#types).
{:shortdesc}

If you have any of the following types of access, you can update this setting for other users in your account:

* Editor or higher role on the User management service
* You are an ancestor in the classic infrastructure hierarchy for the user and you have the Manage users classic infrastructure permission assigned


To turn on this MFA option for a user, the user must set up [security questions](/docs/account?topic=account-login-settings#security-questions) and answers from the profile Login settings page.
{: note}

1. In the {{site.data.keyword.cloud)) console, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user from the list.
3. From the **User details** page in the **Manage user's login** section, set the **Require MFA security questions at login** option to on.

You can manage this setting for yourself if you have the User-managed login setting enabled on your User details page.
{: tip}
