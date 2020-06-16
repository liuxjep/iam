---

copyright:

  years: 2017, 2020

lastupdated: "2020-06-15"

keywords: resource access, assign access, IAM access policy, access to resource groups, edit access, remove access 

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

# Managing access to resources
{: #iammanidaccser}

To manage access or assign new access for users by using IAM policies, you must be the account owner, administrator on all services in the account, or the assigned administrator for the particular service or service instance. For more information about access policies and roles, see [IAM access](/docs/iam?topic=iam-userroles#userroles).
{:shortdesc}


## Editing existing access
{: #edit_existing}
{: help}
{: support}

1. In the {{site.data.keyword.cloud}} console, click **Manage** > **Access (IAM)**, and select **Users**.
2. Select the name of the user that you want to assign access.
3. Select **Access policies**.
4. From the row for the policy that you want to edit, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu, and click **Edit**.
5. Edit the policy.
6. Click **Save**.

To update a user policy by using the CLI, you can use the [**`ibmcloud iam user-policy-update`**](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_user_policy_update) command.
```
ibmcloud iam user-policy-update USER_NAME POLICY_ID [-v, --version VERSION] {-f, --file JSON_FILE | [--roles ROLE_NAME1,ROLE_NAME2...] [--service-name SERVICE_NAME] [--service-instance SERVICE_INSTANCE] [--region REGION] [--resource-type RESOURCE_TYPE] [--resource RESOURCE] [--resource-group-name RESOURCE_GROUP_NAME] [--resource-group-id RESOURCE_GROUP_ID]}
```
{: codeblock}

When you edit access for a user or group, a message stating that duplicate policies aren't allowed might be displayed. 
{: note}

## Assigning new access
{: #assign_new_access}

You can assign access to resources by using two types of policies:

* Access to resources within a resource group, including the option for just one resource or all
* Access to resources in the account, including the option for just one type or all types

If you want to enable a user full administrator access to complete [account management tasks](/docs/iam?topic=iam-account-services#account-services), such as inviting and removing users, viewing billing and usage, managing service IDs, managing access groups, managing user access, and access to all account resources, you must assign a user the following access:
* A policy for **All Identity and Access enabled services** within **All resource groups** with the Administrator and Manager roles for the services and the Administrator role for all resource groups
* Administrator role on **All Account Management Services** 

### Access to resources within a resource group
{: #access_to_resources}

To assign access to all resources in a resource group or to just one service within a resource group, complete the following steps:

1. In the console, click **Manage** > **Access (IAM)**, and select **Users**.
2. From the row for the user that you want to assign access, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu, and click **Assign access**.
3. Add users to an access group. Click **Add** for the access group that you want the users to belong to.
4. (Optional) Manually assign users access.
  1. Expand the Assign users additional access, and click **IAM services**.
  2. Select the option for all services or just a specific service, and then specify if the access is in the **Account**, which means the user doesn't get access to the resource group that contains the resource, or select **All resource groups** or a specific resource group. By selecting a resource group option, you are prompted with roles for access to manage the resource group as well.
  3. Select any combination of roles to assign the user, and click **Add** > **Assign**.

### Access to resources
{: #resourceaccess}

To assign access to an individual resource in the account or access to all resources in the account, complete the following steps:

1. In the console, click **Manage** > **Access (IAM)**, and select **Users**.
2. From the row for the user that you want to assign access, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu > **Assign access**.
3. Add users to an access group. Click **Add** for the access group that you want the users to belong to.
4. (Optional) Manually assign users access.
  1. Expand the Assign users additional access, and click **IAM services**.
  2. Select the option for all services or just a specific service.
  3. Select any combination of roles to assign the user, and click **Add** > **Assign**.

If the user doesn't have a role on the resource group that contains the resources, they can see the resources, but can't work access the resources by going to the Resource list page in the account to start working with them. Assign the Viewer role or higher on the resource group itself to ensure a user can access the resource.
{: note}


## Removing access
{: #removing_access}

Removing access for a user or service ID can take up to 10 minutes to take effect.

1. In the console, click **Manage** > **Access (IAM)**, and select **Users**.
2. Select the user name that you want to remove access for.
3. From the **Access policies** tab, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu on the row for the policy you want to remove, and click **Remove**.  
4. Review the user policy details that you're about to remove, and confirm by clicking **Remove**.

You can also remove users from access groups by selecting the check box of the user you want to remove and click **Remove**. Then click **Remove** again to approve the process. 
{: tip}

To remove a user policy by using the CLI, you can use the [**`ibmcloud iam user-policy-delete`**](/docs/cli?topic=cli-ibmcloud_commands_iam#ibmcloud_iam_user_policy_delete) command.
```
ibmcloud iam user-policy-delete USER_ID POLICY_ID [-f, --force]
```
{: codeblock}


## Reviewing your assigned access
{: #review_your_access}

If you need to review your assigned access in an account that you've been added to, complete the following steps:

1. In the console, click **Manage** > **Access (IAM)**, and select **Users**.
2. Select your name.
3. Review your assigned access in the **Access policies** section.

If you need more access, you must contact the account owner to update your access or contact the administrator for the service or service instance to update the access policy.
