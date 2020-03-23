---

copyright:

  years: 2015, 2020
lastupdated: "2020-03-23"

keywords: application programming interface key, API key, API, classic infrastructure API key, IBM Cloud API key

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Understanding API keys
{: #manapikey}

An application programming interface key (API key) is a unique code that is passed in to an API to identify the calling application or user. API keys are used to track and control how the API is being used, for example to prevent malicious use or abuse of the API. The API key often acts as both a unique identifier and a secret token for authentication, and generally has a set of access that is specific to the identity associated with it.
{:shortdesc}

To view your API keys, go to **Manage** > **Access (IAM)** > **API keys**. 

## {{site.data.keyword.cloud_notm}} API keys for users
{: #ibm-cloud-api-keys}

{{site.data.keyword.cloud}} API keys are associated with the user's identity. Only the user for which the API key is associated with can create and delete it. You can use the {{site.data.keyword.cloud_notm}} API keys in the command-line interface (CLI) or as part of automation to log in as your user identity. You can also use {{site.data.keyword.cloud_notm}} API keys to access classic infrastructure APIs. For more information about using an API key associated with your user identity, see [Managing user API keys](/docs/iam?topic=iam-userapikey#userapikey).


## Other types of API keys
{: #othertypes}

In addition to your {{site.data.keyword.cloud_notm}} API keys, a couple of other types of API keys are available that you might use:

* Service ID API keys
* Classic infrastructure API keys
* Service-specific API keys

You can also use API keys that are associated with service IDs that you create. Service IDs are used to connect an application inside or outside of {{site.data.keyword.Bluemix_notm}} to an {{site.data.keyword.Bluemix_notm}} service. For more information about creating API keys associated with a service ID, see [Managing service ID API keys](/docs/iam?topic=iam-serviceidapikeys#serviceidapikeys).

[Classic infrastructure API keys](/docs/iam?topic=iam-classic_keys) are used to call the APIs for classic infrastructure services. You can create only one classic infrastructure API key at a time. You can create a classic infrastructure API key for yourself from the API keys page or the User details page.

{{site.data.keyword.cloud_notm}} API keys can also be used to access classic infrastructure APIs.
{: tip}

Some services in {{site.data.keyword.Bluemix_notm}} might provide an API key when you work with the service. For example, if you are viewing the offering details of a Watson service by going to the My resources page, you can create a credential that includes an API key and secret that is specific to that service on the Service credentials page.

## Working with API keys

To manage the {{site.data.keyword.Bluemix_notm}} API keys that are associated with your user identity or the ones that you have access to manage for other users in the account, go to **Manage** &gt; **Access (IAM)** &gt; **API keys**. 

On the {{site.data.keyword.cloud_notm}} API keys page, you can create, edit, or delete {{site.data.keyword.cloud_notm}} API keys for yourself, and you can manage all classic infrastructure API keys for users to which you are an ancestor in the user hierarchy. This means you can manage API keys for all users you invited to the account, or your child users invited to the account, and so on. In addition, if you are the account owner or a user with the required access to manage other user's API keys in the account, you can use the **View** filter to list and manage those API keys.

### Required access for managing API keys
{: #API-key-access}

By default, you always have access to create your own API keys, and then update and delete them as needed. You also can manage your own classic infrastructure API key and any users' classic infrastructure API keys who you are an ancestor of in the classic infrastructure user hierarchy, meaning you invited the user or someone you invited to the account invited the user, and so on.

If you are the account owner or a user with the required access, you can access other user's API keys or service ID API keys by using the **View** filter on the API keys page. You can edit or delete the API keys depending on your assigned access. You see only the filter options for the type of API keys that you have access to view and manage.

| Filter Options | Displayed API Keys | Required Access | Allowed Actions |
|-------------------|------------------|------------------|-------------|
| My {{site.data.keyword.cloud_notm}} API keys      | Your {{site.data.keyword.cloud_notm}}  API keys | No access required | View, create, edit, delete |
| All {{site.data.keyword.cloud_notm}} user API keys | All {{site.data.keyword.cloud_notm}}  API keys created by all users in the account | Administrator role on the IAM Identity service | View, edit, and delete |
| All service ID API keys | All API keys created for service IDs in the account | Administrator role on the IAM Identity service | View, edit, and delete |
| Classic infrastructure API keys | Your classic infrastructure API key and any classic infrastructure API keys for users who you are ancestor of in the user hierarchy | No access required other than being an ancestor in the user hierarchy | View details and delete | 
{: caption="Table 1. Required access for API key management on the API keys page" caption-side="top"}
