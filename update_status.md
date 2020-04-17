---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-16"

keywords: user state, user status, change user status, update user status

subcollection: iam

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Updating a user's status
{: #status}

The status for a user depends on if the user accepted their invitation to join the account, if they're a VPN-only user, or if the administrator set the user as a disabled classic infrastructure user.
{:shortdesc}

If you have the following access, you can update the status of another user:

  * An Identity and access management (IAM) policy with Editor or higher role on the User management service.
  * You are an ancestor in the classic infrastructure hierarchy for the user and you have the Manage users classic infrastructure permission assigned

For more information about the types of user status, see [User states](/docs/iam?topic=iam-user_status#user_status).

## Status options
{: #status_options}

You can choose from the following options to update a user's state:

<dl>
<dt>Active</dt>
<dd>The user has full access to the {{site.data.keyword.cloud_notm}} console based on their assigned access policies and classic infrastructure permissions.</dd>
<dt>Disabled classic infrastructure</dt>
<dd>The user can no longer access classic infrastructure resources, but can continue to log in to the console and access platform resources.</dd>
<dt>Suspended</dt>
<dd>The user can log in to the console and view the account in their account list, but can no longer access resources in the account. All information and access policies that are associated with the account are saved.</dd>
<dt>VPN-only</dt>
<dd>The user can't log in to the console, but they can access the devices and VPN subnets that you assign for classic infrastructure by logging in directly to the appliance.</dd>
</dl>

When you update a user from VPN-only status to Active status, the user must know the password to log in to the console. In most cases, the SoftLayer ID password is used, and it might need to be reset to be used. In rare cases where the user already has an IBMid, they must log in with the IBMid and password.
{: note}

## Updating a user's status
{: #update_user_status}

To change a user's status, complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user from the list.
3. From the User details page, select an option from the **User status** menu.  
4. Click **Apply**.
