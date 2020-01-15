---

copyright:

  years: 2018, 2020

lastupdated: "2020-01-14"

keywords: MFA, multifactor authentication, external authentication, order authentication, Symantec, phone-based authentication, cancel authentication order

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Ordering external authentication MFA for a user
{: #external}

As an administrator with the correct access, you can order external authentication and enable the multifactor authentication (MFA) option for a user's login. You are charged a monthly fee for the external authentication options. This type of multifactor authentication (MFA) is required only for the account where the setting is enabled unlike ID-based MFA. For more information, see [Types of multifactor authentication](/docs/iam?topic=iam-types#types).
{:shortdesc}

## Ordering external authentication
{: #ordering}

You can order external authentication for a user if you are the master user or if you have the Manage User and Add/Upgrade Services permissions.

To order external authentication, complete the following steps:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user from the list.
3. From the **User details** page, select **Order external authentication** in the Manage user's login section.
4. Select **Symantec identity protection** or **Phone-based identity protection**.
    * For Symantec authentication, the user must download the [Symantec VIP](https://vip.symantec.com/){: new_window} ![External link icon](../icons/launch-glyph.svg) app and obtain a credential ID to continue with the ordering process.
    * For phone-based authentication, you can proceed with the order, but your user must [set up their configuration](/docs/account?topic=account-login-settings#setting-up-phone-based-authentication) before you can enable the option.
5. Based on your selection, follow the prompts to review the price and terms before you place the order.
6. Click **Order** to finalize your selection.

After Symantec authentication is ordered, you can turn on the option for the user from the User details page. And, after phone-based authentication is ordered and then configured by the user, you can turn on the option for the user from the User details page.

## Disabling external authentication options
{: #disable}

You can disable Symantec or phone-based MFA for a user at any time.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user from the list.
3. From the **User details** page, set the **Symantec authentication** or **Phone-based authentication** option to off.

## Cancelling external authentication options
{: #cancel}

You can cancel your order for external authentication at any time, if you have the correct access. You can choose to cancel immediately without any refund, or you can choose to cancel it at the one year mark from when you ordered it.

To cancel an order for external authentication, you must be an account owner or have all of the following access:

* Manage users classic infrastructure permission
* Cancel services classic infrastructure permission
* Administrator for the Support Center account management service or the view, edit, and add ticket migrated classic infrastructure permissions that are not available within the [migrated permission access groups](/docs/iam?topic=iam-migrated_permissions).

To cancel the external authentication order, complete the following steps:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select Users.
2. Select a user from the list.
3. From the **User details** page, click **Delete** ![Delete icon](../icons/icon_trash.svg) for the **Symantec authentication** or **Phone-based authentication**.
4. Select when to remove it.
5. Click **Remove**.
