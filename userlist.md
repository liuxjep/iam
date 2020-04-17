---

copyright:

  years: 2018, 2020

lastupdated: "2020-04-16"

keywords: user list visibility, users page setting, user view access, limit access to users list, user list access

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# Setting user view access
{: #userlistview}

As an {{site.data.keyword.Bluemix}} account owner, you can view all users in your account and define how users can view other users in the account.
{:shortdesc}

When the **Unrestricted view** option is selected, any user in the account can view other users from the Users page in {{site.data.keyword.Bluemix_notm}} console. When the **Restricted view** option is selected, users can view only specific types of users in the account:

* Users invited by the user
* Users who share a Cloud Foundry org with the user
* Users who are their descendants in the classic infrastructure user hierarchy, meaning the users that they invited or that one of their descendants invited.

By default, the unrestricted view is set for your account. To update this setting, complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** &gt; **Access (IAM)**, and select **Settings**.
2. Select **Restricted view** for the **User list visibility** setting.
