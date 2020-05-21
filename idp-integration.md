---

copyright:

  years: 2020

lastupdated: "2020-05-21"

keywords: identity provider, IdP, App ID, IAM, integration, IdP SSO, third-party authentication, dynamic rules, external identity provider

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Enabling authentication from an external identity provider
{: #idp-integration}

You can integrate with your external identity provider (IdP) to securely authenticate external users to your {{site.data.keyword.cloud}} account. By using your IdP, you can provide a way for users in your company to use single sign-on (SSO). Connecting your cloud account with an {{site.data.keyword.appid_full_notm}} instance of your choice makes it all possible.
{:shortdesc}

Each account can have up to five IdPs added through the Identity providers page in the Access (IAM) section of the console. You set up your IdP by selecting which {{site.data.keyword.appid_short}} instance to integrate with IAM. Then, the IdP is given a random realm ID that is the unique prefix for users of that {{site.data.keyword.appid_short}} service instance. 

Setting up the integration between your {{site.data.keyword.appid_short}} instance, which is already configured with your IdP, and your {{site.data.keyword.cloud_notm}} account makes it so you can continue to manage all users externally in your IdP. It also simplifies the log in process to your cloud account for users in your enterprise. After the integration is complete, you must provide your users with a custom URL that they use to login each time. There is no need to invite anyone to your account because if they exist as a user in your connected IdP's user repository, they can log in with their credentials through the custom URL.

## Before you begin
{: #idp-prereqs}

* Create an instance of {{site.data.keyword.appid_short}} from the {{site.data.keyword.cloud_notm}} catalog. For more information, see the [Getting started tutorial](/docs/appid?topic=appid-managing-idp).
* Configure your {{site.data.keyword.appid_short}} instance. For more information about how to do this depending on your use case, see the {{site.data.keyword.appid_short}} documentation about [managing authentication](/docs/appid?topic=appid-managing-idp).
* Make sure you have the required access to view and manage IdPs, if you aren't the account owner. You must be assigned the operator role or higher on the {{site.data.keyword.appid_short}} instance and the operator or administration role on the [IAM Identity Service](/docs/iam?topic=iam-account-services#identity-service-account-management). 

## Configuration of your {{site.data.keyword.appid_short}} instance for IAM integration
{: #configure-appid-instance}

Review the following requirements about how your {{site.data.keyword.appid_short}} instance must be configured to work properly as an IAM identity provider for your {{site.data.keyword.cloud_notm}} account.

If you plan to use your {{site.data.keyword.appid_short}} instance for IAM identity provider integration, then any user can log in to your account who can authenticate with that {{site.data.keyword.appid_short}} instance. Therefore, consider following these guidelines when you configure your instance:

Disable the following types of authentication:

* Facebook
* Google
* IBMid
* Anonymous

If you decide to use Cloud Directory as an authentication method, disable the option for users to sign up through the app, and instead add only known users individually to your [Cloud Directory](/docs/appid?topic=appid-cloud-directory).
{: tip}

### Setting IAM-specific attributes in {{site.data.keyword.appid_short}} tokens
{: #iam-idp-attributes}

For IAM to work correctly with your external identity provider, you must ensure that the {{site.data.keyword.appid_short}}  instance provides all of the required attributes. See the following table for the required attributes:

| Attribute          | {{site.data.keyword.appid_short}} ID Token Claim            | Source             | Description      |
|--------------------|------------------------------------------------------|--------------------------|-------------------|
| identifier (required)   | id        | {{site.data.keyword.appid_short}} generated     | A unique identifier that identifies a user. It can't be changed during the life time of that user. {{site.data.keyword.appid_short}} creates this identifier. |
| email (required)        | email    | Mapped from SAML assertion "email", which is mandatory for Cloud Directory and SAML configurations. | The user's email address. |
| username (recommended)  | preferred_username if present, otherwise sub    | Mapped from SAML assertion "preferred_username", "username", "user_name" or "userName" if available. Otherwise, the {{site.data.keyword.appid_short}} generated "sub" claim is used | When you work with the CLI, APIs, or the {{site.data.keyword.containerlong_notm}}, the username displays. A username is often an email address, but can also be a different value. If the username is not provided by {{site.data.keyword.appid_short}}, IAM uses the identifier instead. |
| firstname (recommended) | given_name if available, otherwise "notset" as default  | Mapped from SAML assertion "given_name", "givenname", "givenName", "first_name", "firstname" or "firstName" if available, otherwise IAM uses the constant "notset" | The first name of the user that logs in. |
| lastname (recommended)  | family_name if available, otherwise "notset" as default | Mapped from SAML assertion "family_name", "familyname", "familyName", "last_name", "lastname" or "lastName" if available, otherwise IAM uses the constant "notset" | The last name of the user that logs in. |
| name (optional)         | name if present, otherwise built by the firstname, a space, and the last name | There is no automatic mapping from SAML | Full name, including middle initial, title, or anything that is not covered by first name and last name |

When a user authenticates successfully by using the {{site.data.keyword.appid_short}} service instance in the {{site.data.keyword.cloud_notm}} account, the user is automatically added to the account. Added users don't get any access policies assigned by default. However, by using [access groups](/docs/iam?topic=iam-groups) and [dynamic rules](/docs/iam?topic=iam-app-id-dynamic-rules), you can set up automatically assigned access policies.


## Enabling and connecting your identity provider
{: #idp-console}

If you haven't configured any IAM identity providers before in your account, you must enable the IdP login setting for your account first.

1. Enable the IdP login settings for your account. You can skip this step if you've already enabled this setting.
  1. Go to **Manage** > **Access (IAM)** > **Identity providers**, and click **Enable**. 
  2. Enter an alias for the default IdP URL, which you provide to users to log in to your account. 
  
    Since you're sharing the URL with external users, make sure the alias is unique and simple. A common format might be to use your company name or a variation of it.
    {: tip}
     
2. Click **Create** to create your IdP. 
3. Enter a name for the IdP, and select the {{site.data.keyword.appid_short}} instance that you want to connect. Then, select the following options:

  * **Enable for account login?**: Enable your IdPs to be used for users to log in to your account. This option is set by default when you first create an IdP. 
  * **Set as the default?**: When selected, users can use the default IdP URL that you created when you enabled this feature to log in to your account. You can have only one default IdP. For all other IdPs that you create, users must use the realm IDs to log in.
 
4. Click **Create**.

Your IdP is now available on the Identity providers list and the realm ID is generated automatically as the value that represents your IAM identity provider in {{site.data.keyword.cloud_notm}}.
{: note}

## Logging in with external identity provider credentials
{: #log-in-external-idp}

After your {{site.data.keyword.appid_short}} instance is connected to your IdP, and your {{site.data.keyword.appid_short}} instance is integrated with IAM, your users can start logging in to your account. If the IdP is set as the default IdP, then you can share the **Default ID URL** for your account. 

However, since you can have only one set as the default, but you can have up to five set-up in your account, you might need to get the IdP URL for another IdP: 

1. From the Identity provider pages, click the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu for the row of the IdP you need a URL for.
2. Select **View IDP URL**. 
3. Copy the **IdP URL** link to give to users to log in. 


## Using {{site.data.keyword.appid_short}} instances to build dynamic rules in access groups
{: #app-id-dynamic-rules}

In addition to the required and recommended attributes, you can pass any kind of information with your SAML assertion. These attributes are available for you to use in [dynamic rules in access groups](/docs/iam?topic=iam-rules).

To successfully build a dynamic rule, the following information is required:

* Identity provider: Use the prefix `appid://` and the realm ID from the IAM identity provider. For example, `appid://A1B2C3D4` if the realm ID of the user was `A1B2C3D4`.
* Add users when: Use the name of the additional SAML assertion. This property is passed through unchanged.
* If you are using the Cloud Directory option or the SAML federation option in {{site.data.keyword.appid_short}}, notice that you can add custom attributes to each user's profile. You can use those properties for dynamic rules too. However, if you have the same property as a custom attribute and as a SAML assertion, then the custom attribute from the SAML assertion is used.

The {{site.data.keyword.containerlong_notm}} up to release 1.18 relies on unique usernames in an account. To work correctly, you must ensure that all usernames are unique across all identity providers. This means that you must make sure that the usernames that are onboarded to your account from IBMid and users that are onboarded to your account by an IAM identity provider don't overlap. Otherwise, the {{site.data.keyword.containerlong_notm}} RBAC rules might get confused and give incorrect permissions.
{: note}

If you are working with an external identity provider, it is recommended that you connect with one external identity provider only and let users onboard automatically through this identity provider. 

Don't invite users by using the {{site.data.keyword.cloud_notm}} invite process since this works only for users with IBMids. If you used {{site.data.keyword.cloud_notm}} invites for your account, you would end up with a mixture of users coming from IBMid and users being automatically onboarded from your external identity provider. This can easily lead to confusion because IBMid users log in through the {{site.data.keyword.cloud_notm}} website while users from your external identity provider must log in with a special URL. This can lead to duplicate usernames in one account, which is strongly discouraged due to limitations in the {{site.data.keyword.containershort}} as previously mentioned.
{: tip}

