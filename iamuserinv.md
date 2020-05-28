---

copyright:

  years: 2015, 2020

lastupdated: "2020-04-16"

keywords: invite, invite users, invitation access, vpn-only user

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}  
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}

# Inviting users to an account
{: #iamuserinv}

Use {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) to invite users, cancel invitations, or resend a pending invitation. You can invite a single user or multiple users.
{:shortdesc}

## Before you begin
{: #invite-access}

To invite users and manage outstanding invitations, you must have at least one of the following types of access:

* Account owner
* Cloud Foundry organization manager
* An IAM access policy with the Editor role or higher on the user management account management service
* The Manage Users classic infrastructure permission to add users

Depending on your access level, you can invite new users and assign all or just some types of access. For example, if you're not the account owner, but you're a Cloud Foundry organization manager, you can invite users and assign only Cloud Foundry access.
{: note}

## Setting up an invitation
{: #invitations}
{: help} 
{: support}

To invite users, complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} console, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Click **Invite users**.
3. Specify the email addresses of the users. If you are inviting more than one user with a single invitation, they are all assigned the same access.
4. Add one or more of the access options that you manage. You must assign at least one access option. For any access options that you don't add and configure, the default value of **No access** is assigned. Depending on the options that you are authorized to manage, you can assign the following types of access:

  * Add users to access groups. Click **Add** for each access group that you want the users to belong to. 
  * Manually assign users access. Expand this section to assign individual IAM access policies, Cloud Foundry roles, or classic infrastructure permissions.
     * Select **Cloud Foundry**, choose an organization, then select a region to select a specific space, and assign a space role. An organization and space role are both required to add the access assignment to the invite.
     * Select **Classic infrastructure**, and then choose from the three permission sets.
     * Select **IAM services**, and then select the option for all services or just a specific service. Next, you can scope the access to the entire account, all resource groups, or just one resource group. Then, select all roles that apply. To view what actions are mapped to each role, click the **Actions for role** option to view a list of all actions that are mapped to a specific role. <br><br> Some services support the use of advanced operators to grant access to resources that satisfy specific naming conventions. See [Assigning access by using wildcard policies](/docs/iam?topic=iam-wildcard) for more information. 
     
         If you select the **Account** scope for the access policy, the user must already have the Viewer role or higher on the resource group or groups that contain the resources you want the user to have access to. Without a role on a resource group, the user can't work with the resource from the Resource list page in the console.
         {: tip}
     
     * Select **Account management**, and then choose from the all account management services option or select a specific service. Then, select all roles that apply.
     
5. Select **Add** to save the access assignment to the invitation.
6. After you add all the necessary access assignments, click **Invite**.

You can cancel an invitation for any users that are shown in a Processing or Pending state in the Status column. If an invited user did not receive an invitation, you can resend the invitation to any user in a Pending state.
{: note}

### Inviting users by using the CLI
{: #cli-invite}

To invite users by using the command-line interface (CLI), run the following command:

```
ibmcloud account user-invite USER_EMAIL [-o ORG [--org-role ORG_ROLE] [-s SPACE, --space-role SPACE_ROLE]]
```

By using the CLI, you can choose to assign Cloud Foundry access or no access and work on assigning access later. For more information about the command parameters, see [**`ibmcloud account user-invite`**](/docs/cli?topic=cli-ibmcloud_commands_account#ibmcloud_account_user_invite). 

### Inviting users by using the API
{: #api-invite}

You can use the [API](https://cloud.ibm.com/apidocs/user-management#invite-users){: external} to invite users in bulk. All users that are included in a single invitation are assigned the same access. When you invite users by using the API, you enter emails in a comma-separated list with each entry that is surrounded by quotations, for example:


```
curl -X POST \
  https://user-management.cloud.ibm.com/v2/accounts/987d4cfd77b04e9b9e1a6asdcc861234/users \
  -H 'Authorization: Bearer <IAM_TOKEN>'
  -H 'Content-Type: application/json' \
    -d '{
      "users": [
            {
              "email": "cloud_api_example_member@ibm.com",
              "account_role": "Member"
            },
            {
              "email": "second_user@ibm.com",
              "account_role": "Member"
            },
            {
              "email": "third_user@ibm.com",
              "account_role": "Member"
            }
      ],
      "iam_policy": [
      {
        "roles": [
        {
          "id": "crn:v1:bluemix:public:iam::::role:Viewer"
        }],
        "resources": [
        {
          "accountId": "111d4cfd77b04e9b9e1a6asdcc861234",
          "resourceType": "resource-group",
          "resource": "111449dd871049c29ec3a53853ce123e"
        }]
      }]
    }'
```
{: codeblock}


## Adding VPN-only users
{: #add-vpn-only}

Any user with the following permissions can add a VPN-only user:

- For Cloud Foundry, you must have the Manager organization role. 
- For classic infrastructure, you must have the Manage Users permission on the account.
- For IAM access, you must have the Administrator or Editor role on the user management account management service. 

To add a VPN-only user, use the following steps:

1. On the Users page, click **Add VPN-only user**.
2. Enter the personal information details for the user.
3. Click **Save**.
