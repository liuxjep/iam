---

copyright:

  years: 2018, 2020

lastupdated: "2020-04-16"

keywords: parent user, change parent user, classic infrastructure hierarchy

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Updating a user's parent user
{: #update-parent}

If you have the correct access, you can update the parent for a user. Updating the parent user affects how a user sees other users in the account when the setting for user list visibility is set to restricted. Users see only other users for which they are a parent and any other users who are invited by those descendants of the parent user.
{:shortdesc}

For more information about the setting, see [Setting user view access](/docs/iam?topic=iam-userlistview#userlistview).

If you have the following access, you can update the parent for another user:

* An IAM policy with Editor or higher role on the User management service.
* You are an ancestor in the classic infrastructure hierarchy for the user and you have the Manage user classic infrastructure permission assigned


To update a user's parent, complete the following steps:

1. In the {{site.data.keyword.Bluemix}} console, click **Manage** &gt; **Access (IAM)**, and select **Users**.  
2. Select a user name from the list.
3. From the User details page, select a new parent user from the **Parent** menu.
4. Click **Apply**.
