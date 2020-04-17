---

copyright:

  years: 2018, 2020

lastupdated: "2020-04-16"

keywords: login settings, manage user login settings, change login settings for user

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}

# Managing a user's login settings
{: #loginsettings}

An account owner, or a user that has the correct access, can manage a user's login settings, for example, order external authentication options, enable a one-time passcode to be used during login, enable the use of security questions at login, and set a password expiration time period.
{:shortdesc}

Complete the following steps to manage the login settings for a specific user:

1. In the {{site.data.keyword.cloud}} console, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user from the list, and click **User details**.
3. From the **Manage user's login** section, you can turn the following options on or off for the selected user:

    * Time-based one-time passcode MFA: Turn this option on to enable the user to be prompted for the one-time passcode at login. The user must set up their TOTP MFA from the Login settings page. For more information, see [Enabling one-time passcode MFA for a user](/docs/iam?topic=iam-totp#totp).

    * Order external authentication: Select this option to purchase Symantec or phone-based authentication for a monthly cost. Only one option can be ordered and used at a time. For more information, see [Ordering external authentication MFA for a user](/docs/iam?topic=iam-external#external).

        * Phone-based authentication: The user can use this option by using the configuration that they set up from the User details page after the account owner orders it.
        * Symantec authentication: The user can use option after the account owner orders it. In order for an administrator to order this option, the user must provide their credential ID first.

    * MFA Security questions at login: Turn this option on to require a user to be prompted for the security questions and answers that they set up from the Login settings page. You can't turn this option on unless the user has already set up their security questions. For more information, see [Enabling MFA security questions for a user](/docs/iam?topic=iam-questions#questions).

    * User-managed login: Turn this option on to enable the user to set a password expiration, turn on security questions for login, and specify allowed IP addresses for {{site.data.keyword.cloud_notm}} login and classic infrastructure APIs.

    * Password expiration: Set an expiration by selecting an option from the list. This option is available only for users with a SoftLayer ID. If the user can manage their own login settings, they can set this expiration on their Login settings page. Only users with the following permissions can set a password expiration for a user:

        * Any user assigned an IAM policy with the Editor or higher role on the User management service.
        * Any user who has User-managed login enabled on their User details page by their administrator.
        * Any ancestor in the classic infrastructure hierarchy for the user with the Manage users classic infrastructure permission assigned.

Only one MFA option should be enabled at a time. If IBMid MFA is required for any account that the user is a member of, it overrides any other MFAs that are enabled, and the user is not prompted for any other type of MFA.
{: important}
