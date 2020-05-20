---

copyright:
  years: 2015, 2020
lastupdated: "2020-05-20"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Troubleshooting for IAM
{: #troubleshoot_iam}

General problems with using Identity and Access Management (IAM) might include needing access to a resource or account to complete a task or identifying the right type of access to assign users in your account to complete specific tasks. In many cases, you can recover from these problems by following a few steps.
{:shortdesc}

## I gave a user access to a resource, but they still can't access it from the Resource list page
{: #troubleshoot-serviceaccess}
{: troubleshoot}

A user has an access policy on a specific resource or a service in the account, but they can't access the service from the My resources page.

When the user selects the service name, the following error message is displayed:
{: tsSymptoms}

`You do not have access to any organizations, spaces, or resource groups in this region. Check that you have the appropriate access with your account owner or administrator.`

   
In addition to access to the type of service or specific resource, the user must also be assigned access to the resource group or space that contains the resource. To access the resource instance within a specific account, a user must be assigned at least the Viewer role or higher on the resource group itself. 
{: tsCauses}

1. In the {{site.data.keyword.cloud_notm}} console, go to **Manage** &gt; **Access (IAM)**, and select the user's name from **Users** page. 
1. From the row for the user that you want to assign access, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu, and click **Assign access**.
1. Select **Assign users additional access**.
1. Select the **IAM services** tile. 
1. Select the type of access you want to assign, then select a specific resource group if you want to limit the user to view or manage only resources in that resource group, or select **All resource groups**. 
1. Next, select the role that you want the user to have. The Viewer role is sufficient to enable the user to access the resource. 
1. Click **Add** to add the access to the access summary. 
1. Click **Assign**. 
{: tsResolve}

For more information about what other actions a user can perform with a policy on the resource group itself, see [Assigning access to resource groups and the resources within them](/docs/resources?topic=resources-bp_resourcegroups#assigning_access_rgs).


## How do I know what access I am assigned?
{: #troubleshoot-myaccess}
{: troubleshoot}

If you don't have access to complete a particular task, such as creating a service instance and adding it to a resource group or inviting other users to the account, you might need to check what access you are assigned.

I'm not sure what level of access I'm assigned to complete actions in an account of which I am a member. 
{: tsSymptoms}
   
You might not be assigned the correct access. 
{: tsCauses}

To check what you have access to and the level of access, complete the following steps. If you need to request access, contact the account owner.

Go to **Manage** &gt; **Access (IAM)** in the console, and select your name on the **Users** page. Then, depending on the access you're looking for, select the different tabs:
{: tsResolve}

* To determine what access you have through the access groups you are assigned, select **Access groups**.
* To see IAM access policies that are assigned to you, select the **Access policies**.
* To see your Cloud Foundry access for all orgs and spaces, select **Cloud Foundry access**.


## How can I get access to invite users to the account? 
{: #troubleshoot-invite}
{: troubleshoot}

If you are not the account owner and aren't assigned the correct access, then you can't invite users to an account. 

I can't invite users to the account.
{: tsSymptoms}
   
You might not be assigned the correct access. 
{: tsCauses}

To invite users and manage outstanding invitations, you must be an account owner, an organization manager, a user with an IAM access policy with Editor or higher role on the user management account management service, or you must have classic infrastructure permissions to add users.
{: tsResolve}


## How can I view classic infrastructure permissions for other users?
{: #troubleshoot-classicinfra}
{: troubleshoot}

Account owners have full access to the account, so they do not see the permissions for themselves. Individual users can't edit their own permissions, so they see permissions on their classic infrastructure page, but can't edit them. You must have specific access to view and edit permissions for another user in the account.

You see a message that states that you can't view another user's classic infrastructure permissions.
{: tsSymptoms}
   
You might not be assigned the correct access.
{: tsCauses}

You must ask the account owner to be assigned the **Manage users** classic infrastructure permission, but you must also be an ancestor of the user within the classic infrastructure user hierarchy to view and manage another user's permissions.
{: tsResolve}

## How can I manage migrated billing and support case permissions in IBM Cloud?
{: #troubleshoot-migrated-permissions}
{: troubleshoot}

With the initial migration of users and permissions for managing billing and support cases from your SoftLayer account to your linked {{site.data.keyword.Bluemix_notm}} account, some users might not have these permissions. However, all migrated permission access groups are now assigned the correct IAM access policies, ensuring that all users are assigned the correct access that they had previously.

Users don't seem to have the same managing billing and support case permissions in the {{site.data.keyword.Bluemix_notm}} console that they were previously assigned in your SoftLayer account.
{: tsSymptoms}
   
Your migrated permissions access groups might not be assigned the correct access policies when the users were initially migrated.
{: tsCauses}

As of 20 May 2019, all [migrated permission access groups](/docs/iam?topic=iam-migrated_permissions) have the correct policies that are assigned for managing billing information and support cases. If you tried to use these groups before this date, the access groups that are missing equivalent IAM access policies might have caused a mismatch in the assigned access between the SoftLayer permissions and IAM access. This is resolved. You can go to **Manage** > **Access (IAM)** in the console, and then select **Access groups** to review the users and policies that are assigned to each access group.
{: tsResolve}

## I can't assign access in my account because I reached the maximum number of allowed policies
{: #troubleshoot-policy-limit}
{: troubleshoot}

I tried to assign access, but received an error message that I reached the limit of access policies in the  account.

A new policy can't be created to assign access, and I receive an error message that states `422: Exceeded maximum policies quota error`.
{: tsSymptoms}
   
The account is at the [limit of total number of policies allowed](/docs/iam?topic=iam-iam_limits).
{: tsCauses}

Reduce the number of policies on the account by following the [Best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup). For more information about policy limits for the account, see [IBM Cloud IAM limits](/docs/iam?topic=iam-iam_limits).
{: tsResolve}

## I can't manage a service ID that I created and previously had access to
{: #troubleshoot-serviceid-access}
{: troubleshoot}

I don't have access to manage a service ID that I created in an account where I am not the owner. I received an error message about not having the required access, but I used to be able to manage it. 
{: tsSymptoms}

If you create a service ID in an account that you don't own, an administrator policy for that specific service ID is automatically generated for you only if you don't already have access to manage service IDs in the account. For example, if you are already assigned the Administrator role on the IAM Identity service, then a new policy is not automatically generated because you already have access. However, if the account administrator later revokes your access as an administrator on the IAM Identity service, then you can no longer manage the service IDs that you created in the account.
{: tsCauses}

Request the correct level of access from the account administrator to manage all service IDs in the account or just the specific ones that you created. 
{: tsResolve}

