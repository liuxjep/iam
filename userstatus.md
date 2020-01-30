---

copyright:

  years: 2017, 2020

lastupdated: "2020-01-30"

keywords: user state, user status, type of user

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}


# User status
{: #user_status}

All account users are assigned a status that describes their user state. A user's status is displayed on the User details page. For more information about changing a user's status, see [Updating a user's status](/docs/iam?topic=iam-status#status).
{:shortdesc}

| User State                      | Description                                                                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Active                          | The user accepted the invitation and has the assigned access to work within the account.                                                                      |
| Disabled classic infrastructure | The account owner or a user with sufficient permissions can set another user as disabled so that the user can no longer access classic infrastructure resources. The user can continue to log in to the console and access platform resources or support cases. |
| Invalid                   | A user's IAMid is deleted, and they can't access IAM-enabled resources. The user retains VPN access and can still use their classic infrastructure API key, but can't log in to the console. | 
| Pending                         | A state in which a user is invited but hasn't accepted the invitation or joined the account by creating an {{site.data.keyword.Bluemix_notm}} account. |
| Processing                      | A rarely viewed state in which the user is added to an invite, the system creates the first instance of the user, but the invite hasn't been sent.    |
| Suspended                       | The account owner or a user with sufficient permissions can set another user as suspended so that the user can no longer access resources in the {{site.data.keyword.Bluemix_notm}} account. This is a temporary alternative to removing a user. No information or policies that are associated with the account are removed. |
| VPN-only                        | A user that is created in the account, but is restricted to VPN access only for devices. This type of user doesn't have access to log in to the console.      |
{: caption="Table 1. User status" caption-side="top"}
