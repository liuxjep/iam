---

copyright:

  years: 2019

lastupdated: "2019-09-25"

keywords: account management, access, access policy, account administrator, user management, account management services, use account management services to grant users in the account access to invite users to the account, billing service, support center service, identity service, global catalog service, enterprise service

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Assigning access to account management services
{: #account-services}

As the account owner or the administrator of an account management service, you can use these services to grant users access to complete tasks such as invite users to the account, track billing and usage, and work with support cases. Users with account management access policies can also manage service IDs, access policies, catalog entries, and access groups.
{:shortdesc}

## Creating policies for account management service access
{: #account-management-access}

To assign access to one or all account management services, complete the following steps:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and then select **Users**.
2. From the row for the user that you want to assign access, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu, and then click **Assign access**.
3. Select to assign access to **Account Management Services**.
4. Select **All Account Management Services** or select a specific account management service.
5. Select any combination of roles to assign the wanted access.

To grant another user full access to the account for the purposes of managing user access and all account resources, you must assign two policies. One policy that gives the user access to all resources in the account by selecting **All Identity and Access enabled services** with the **Administrator** and **Manager** role assigned. And, one policy that gives the user access to all account management services in the account by selecting **All account management services** with the **Administrator** role assigned.
{: tip}

## Actions and roles for account management services
{: #account-management-actions-roles}

The following tables outline the actions that users can take when they are assigned a specific role for each account management service. Review the information to ensure that you are assigning the correct level of access to your users. 

### Access groups
{: #access-groups-account-management}

You can give users access to view, create, edit, and delete access groups in the account by using the access groups account management service. 

| Roles | Actions |
|:-------|----------|
| Viewer |   View access groups and members     |
| Operator | Not applicable    |
| Editor |  View, create, edit, and delete groups <br><br> Add or remove users from groups     |
| Administrator |  View, create, edit, and delete groups <br><br> Add or remove users <br><br> Assign access to a group <br><br> Manage access for working with access groups   |
{: caption="Table 1. Roles and example actions for the Access groups service" caption-side="top"}

### User management
{: #user-management-account-management}

You can give users access to view users in an account, invite and remove users, and view and update user profile settings with the user management account management service. 

| Roles | Actions |
|:-------|----------|
| Viewer |  View users in the account <br><br> View user profile settings     |
| Operator | View users in the account <br><br> View user profile settings  |
| Editor |  View, invite, remove, and update users from the account <br><br> View and update user profile settings    |
| Administrator | View, invite, remove, and update users from the account <br><br> View and update user profile settings    |
{: caption="Table 2. Roles and example actions for the User Management service" caption-side="top"}

The viewer role on the user management service is a commonly assigned role for users also being assigned a role to view or manage support cases. This is because if an account owner restricts the visibility of the user list in the IAM settings, it can cause users to not be able to see support cases opened by other users in the account. However, if they are assigned the viewer role for the user management service, the user list visibility setting doesn't affect their ability to view cases in the account
{: tip}

### Support center
{: #support-center-account-management}

You can give users access to manage support cases by using the support center service.

| Roles | Actions |
|:-------|----------|
| Viewer |  View cases <br><br> Search cases      |
| Operator |  Not applicable    |
| Editor |  View cases <br><br> Search cases <br><br> Update cases <br><br> Create cases     |
| Administrator |  View cases <br><br> Search cases <br><br> Update cases <br><br> Create cases    |
{: caption="Table 3. Roles and example actions for the Support Center service" caption-side="top"}

It is common to assign users the viewer role on the user management service in addition to a support center access policy to ensure that users can see all cases in the account regardless of how the account owner has set the user list visibility setting. If the user list visibility setting is set to restricted, making it so users are restricted from seeing other users in the account, this can limit a user's ability to view, search, and manage support cases in an account that they did not open themselves.
{: tip}

### Billing
{: #billing-acct-mgmt}

You can give users access to update account settings, view subscriptions, view offers, apply subscription and feature codes, update spending limits, and track usage by using the billing service.

| Roles | Actions |
|:-------|----------|
| Viewer | View account feature settings <br><br> View subscriptions in account <br><br> View account name |
| Operator | View account feature settings <br><br> View subscriptions in account <br><br> View and change account name    |
| Editor |  View and update account feature settings <br><br> View subscriptions in account <br><br> View offers in account <br><br> View and apply subscription and feature codes <br><br> View and change account name <br><br> View and update spending limits  |
| Administrator |  View and update account feature settings <br><br> View subscriptions in account <br><br> View offers in account <br><br> View and apply subscription and feature codes <br><br> View and change account name <br><br> View and update spending limits <br><br> View subscription balances and track usage <br><br> Create an enterprise  |
{: caption="Table 4. Roles and example actions for the Billing service" caption-side="top"}

### IAM identity service
{: #identity-service-account-management}

You can give users access to manage service IDs by using the IAM identity service. For the IAM identity service, these actions apply to service IDs within the account that the user didn't create. All users can create service IDs. They are the administrator for those IDs, and they can create the associated API key and access policies. However, this account management service applies to the ability to view, delete, and assign access to service IDs in the account created by other users.

| Roles | Actions |
|:-------|----------|
| Viewer |   View IDs     |
| Operator | Create and delete IDs and API keys   |
| Editor |  Create, update, and delete IDs and API keys  |
| Administrator |  Create, update, and delete IDs and API keys <br><br> Assign access policies to IDs  |
{: caption="Table 5. Roles and example actions for the IAM Identity service" caption-side="top"}
{: #identity-service-acct-mgmt}


### Global catalog
{: #global-catalog-account-management}

You can give users access to view private services in the catalog or change the visibility for others users for private services by using the global catalog service.

| Roles | Actions |
|:-------|----------|
| Viewer |   View private services    |
| Operator | Not applicable    |
| Editor |   Change object metadata but can't change visibility for private services     |
| Administrator |  Change object metadata or visibility for private services, and restrict visibility of a public service   |
{: caption="Table 6. Roles and example actions for the Global Catalog service" caption-side="top"}


### Enterprise
{: #enterprise-account-management}

You can use the enterprise service to assign users access to manage an enterprise by creating accounts within the enterprise, assigning accounts to account groups, naming account groups, and more. This type of policy works only if it is assigned within the enterprise account. 

| Roles | Actions |
|:-------|----------|
| Viewer |  View the enterprise, account groups, and accounts    |
| Operator |  View the enterprise, account groups, and accounts    |
| Editor |  View and update the enterprise including the name and domain, create accounts and account groups, view usage reports, and import accounts. |
| Administrator |  View and update the enterprise including the name and domain, create accounts and account groups, move accounts between account groups, import existing accounts, and view usage reports  |
| Usage report viewer | View the enterprise, accounts, and account groups and view usage reports for all accounts in the enterprise. |
{: caption="Table 7. Roles and example actions for the Enterprise service" caption-side="top"}


### License and entitlement 
{: #license-entitlement-management}

You can use the license and entitlement service to assign users access to manage licenses and entitlements within an account. Any member of an account can view and use an account’s entitlement.  
 
| Roles | Actions |
|:-------|----------|
| Viewer |  Not applicable     |
| Operator |  Not applicable     |
| Editor |  Editors can create entitlements and view, update, bind, or delete only the entitlements they acquired. |
| Administrator |  Administrators can create entitlements and view, update, bind, or delete any entitlements in the account. |
{: caption="Table 8. Roles and example actions for the license and entitlement service" caption-side="top"}

### All account management services option
{: #all-account-management}

To quickly give users a wide-ranging set of account management access, you can assign a policy on the all account management services option. Depending on the role that is selected, all applicable actions per the selected role for each account management service can be completed by the subject of the policy.


| Roles | Actions |
|:-------|----------|
| Viewer |  All viewer role actions for the account management services     |
| Operator |  All operator role actions for the account management services     |
| Editor |  All editor role actions for the account management services and the ability to create resource groups    |
| Administrator |  All administrator role actions for the account management services and the ability to create resource groups   |
{: caption="Table 9. Roles and example actions for a policy on all identity and access services" caption-side="top"}
