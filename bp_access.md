---

copyright:

  years: 2018, 2019
lastupdated: "2019-12-13"

keywords: advantage of access groups, access assignment process, assign access, best practice, access management, strategy

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}

# Best practices for assigning access
{: #account_setup}

To streamline the access assignment process, you can take advantage of access groups to assign a minimal number of policies by giving the same access to all users and service IDs that belong to the same access group. Use these best practices to learn more about providing users access to resources, resource groups, and account management services.
{:shortdesc}

To ensure that your account is fully set up for success, check out [Best practices for setting up your account](/docs/account?topic=account-account_setup#account_setup) and [Best practices for organizing resources in resource groups](/docs/resources?topic=resources-bp_resourcegroups#bp_resourcegroups).
{: tip}

## What is a good access group strategy?
{: #rg_strategy}

An access group is a grouping of user and service IDs to which the same IAM access can be granted. You can assign a single policy to the group instead of assigning the same access multiple times per individual user or service ID.

Assuming you followed the [best practices for setting up your account](/docs/account?topic=account-account_setup#account_setup), a logical way to assign access is by creating one access group per wanted level of access. Then, you can map each access group to the previously created resource groups. For example, to control access to the `CustApp` project, you might create the following access groups:

* Auditor-Group
* Developer-Group
* Admin-Group

For the Auditor-Group, assign two access policies that grant viewer access to the `CustApp-Test` and the `CustApp-Prod` resource groups. For the Developer-Group, assign two access policies that grant editor access to the `CustApp-Dev` and `CustApp-Test` environments. For the Admin-Group, assign three access policies that grant administrator access to all three `CustApp` resource groups.

Though these suggestions are designed for a hypothetical scenario, you can configure the access group to resource group mapping as you see fit.

## Creating access groups
{: #access-group-setup}

To create an access group, complete the following steps:

1. In the {{site.data.keyword.Bluemix}} console, click **Manage** &gt; **Access (IAM)**, and select **Access Groups**.
2. Click **Create**.
3. Enter the name and description for the group.
4. Click **Create**.

After you create an access group, you can add users and service IDs to the group.

## How IAM access policies provide access
{: #how_access}

A policy consists of a subject, target, and role. The subject in this case is the access group. The target is what you want the subject to access, such as a set of resources, a service instance, all services in the account, or all instances of a service. The role defines the level of access that is granted to a user.

The most commonly used roles are viewer, editor, and administrator. The viewer role provides the least amount of access for viewing instances and resource groups in an account. The editor role has more access for creating, editing, deleting, and binding service instances. The administrator role includes everything for working with a service instance and can assign access to others. However, two different categories of roles are available to consider: platform and service. For more information about the roles that can be assigned, see the [IAM roles](/docs/iam?topic=iam-userroles#iamusermanrol).

## Assigning access to access groups
{: #assigning-access}

You can organize resources in a resource group and users and service IDs into an access group to make assigning access as simple as possible. After you set up each one, you can create access policies for the access groups to give users in your account access to the resources that you created.

1. Click **Manage** &gt; **Access (IAM)**, and select **Access Groups**.
2. Select the name of the access group that you want to assign access.
3. Select the **Access policies** tab, and then click **Assign access**. 
4. Select the type of access that you want to assign. <br><br> Some services support the use of advanced operators to grant access to resources that satisfy specific naming conventions. See [Assigning access by using wildcard policies](/docs/iam?topic=iam-wildcard) for more information. 

  If you select the **Account** scope for the access policy, the user must already have the Viewer role or higher on the resource group or groups that contain the resources you want the user to have access to. Without a role on a resource group, the user can't work with the resource from the Resource list page in the console.
  {: tip}

5. Click **Add** > **Assign**. 

Easily give multiple users administrator access to everything in an account by creating an access group and assigning two policies to it. To create the first policy, use the **IAM services** option, and select **All Identity and Access enabled services** with the administrator role assigned. To create the second policy, use the **Account Management** option, and select **All Account Management Services** with the administrator role assigned.
{: tip}
