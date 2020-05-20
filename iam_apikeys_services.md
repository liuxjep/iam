---

copyright:

  years: 2018, 2019

lastupdated: "2019-05-20"

keywords: IBM Cloud service APIs, IAM token, API key, authenticate with service API

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Invoking {{site.data.keyword.cloud_notm}} service APIs
{: #iamapikeysforservices}

To invoke an {{site.data.keyword.Bluemix}} service through an API, pass your credentials to the service's API to authenticate your user identity and your access to perform actions within the context of the service.
{:shortdesc}

You can identify the caller in one of the following ways:

* {{site.data.keyword.Bluemix_notm}} API key or service ID API key
* {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) token

[{{site.data.keyword.Bluemix_notm}} API keys](/docs/iam?topic=iam-userapikey#userapikey), [service ID API keys](/docs/iam?topic=iam-serviceidapikeys#serviceidapikeys), and IAM tokens uniquely identify the caller’s identity.  The caller identity is either an {{site.data.keyword.Bluemix_notm}} user or a service ID that was created in an {{site.data.keyword.Bluemix_notm}} account.

The API keys are credentials that consist of a long series of random characters or numbers. An {{site.data.keyword.Bluemix_notm}} identity can have multiple API keys. Each of these API keys can be managed independently, meaning if this API key is used by your service only, you can delete the API key without disrupting some other component.

You can use API keys to [log in to the {{site.data.keyword.Bluemix_notm}} command-line interface (CLI)](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) or to [generate IAM tokens](/docs/iam?topic=iam-iamtoken_from_apikey#iamtoken_from_apikey). While it is not recommended for production use, you can also send API keys to {{site.data.keyword.Bluemix_notm}} services.

## Passing an {{site.data.keyword.Bluemix_notm}} API key to authenticate with a service API
{: #apikey_auth}

API clients can directly pass an {{site.data.keyword.Bluemix_notm}} API key to the target service’s API. To do so, send the `apikey` keyword as the user name and the {{site.data.keyword.Bluemix_notm}} API key as the password by using basic authorization HTTP header to the target service.

The target service API must introspect the {{site.data.keyword.Bluemix_notm}} API key by using the {{site.data.keyword.Bluemix_notm}} IAM service. The following graphic shows three API interactions. The {{site.data.keyword.Bluemix_notm}} API key is passed to every target service’s API, so each target service must look up the {{site.data.keyword.Bluemix_notm}} API key details by invoking {{site.data.keyword.Bluemix_notm}} IAM.

![Authenticating with a service API by using an API key](images/APIkeyauth.svg "Passing API keys to target services which then pass the API key to IAM to validate credentials"){: caption="Figure 1. Passing API keys to target services which then pass the API key to IAM to validate credentials" caption-side="bottom"}

Using an {{site.data.keyword.Bluemix_notm}} API key is convenient, and it makes it easy to discover new APIs and quickly try out prototypes. This method requires you to send the {{site.data.keyword.Bluemix_notm}} API key to the target service‘s API in a readable format, which unnecessarily compromises the API key. Additionally, as the target service’s API must always introspect the API key, this method is less performant and therefore not recommended for production work loads.

To authenticate with a service's API by using an API key, complete the following steps:

  1. First, [create an {{site.data.keyword.Bluemix_notm}} API key](/docs/iam?topic=iam-userapikey#create_user_key) if you have not already.
  2. Send the {{site.data.keyword.Bluemix_notm}} API key as defined in [RFC 7617](https://tools.ietf.org/html/rfc7617){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") as HTTP header “Authorization”. Use `apikey` as the user name, and the API key value as the password.

As an example, the following steps assume that the API key is 0a1A2b3B4c5C6d7D8e9E:

  1.	Concatenate the user name `apikey` and the API key separated by a colon: `apikey:0a1A2b3B4c5C6d7D8e9E`
  2.	Base64 encode the string: `base64("apikey:0a1A2b3B4c5C6d7D8e9E") => YXBpa2V5OjBhMUEyYjNCNGM1QzZkN0Q4ZTlF`
  3.	Set the HTTP header Authorization with schema Basic, for example `Authorization: Basic YXBpa2V5OjBhMUEyYjNCNGM1QzZkN0Q4ZTlF`. When you use the curl command, you can pass this with the parameter -u:

    ```
    curl -u "apikey:<IBM Cloud API key value>"
    ```

  If you use other tools, you might have to specify these credentials differently.
  {: tip}

## Passing an {{site.data.keyword.Bluemix_notm}} IAM token to authenticate with a service's API
{: #token_auth}

To retrieve an IAM access token, the API client must first invoke an {{site.data.keyword.Bluemix_notm}} IAM API to authenticate and retrieve that token. The preferred way for {{site.data.keyword.Bluemix_notm}} service API clients is to use an {{site.data.keyword.Bluemix_notm}} API key to get an IAM access token. The IAM access token can be used for multiple invocations of {{site.data.keyword.Bluemix_notm}} services that accept IAM access tokens as an authentication method. As IAM access tokens are digitally signed with asymmetric keys, {{site.data.keyword.Bluemix_notm}} services can validate an IAM access token without invoking any external service. This dramatically improves the performance of invoking an API.

![Authenticating with a service API by using an access token](images/tokenauth.svg "Retrieving a token from IAM by using an API key and passing the access token to target services to validate credentials"){: caption="Figure 2. Retrieving a token from IAM by using an API key and passing the access token to target services to validate credentials" caption-side="bottom"}

To authenticate with a service's API by using an access token, complete the following steps:

  1. First, [create an {{site.data.keyword.Bluemix_notm}} API key](/docs/iam?topic=iam-userapikey#create_user_key) if you have not already.
  2. The next step for the API client is the retrieval of an IAM access token, as described in [Getting an IAM token from an API key](/docs/iam?topic=iam-iamtoken_from_apikey#iamtoken_from_apikey).
  3. From the response, extract the property `access_token` to get the IAM access token. `expires_in` indicates the seconds until the IAM access token `access_token` expires. Either use this relative value or the absolute time stamp `expiration` based in [UNIX time](https://en.wikipedia.org/wiki/Unix_time){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
  4. Send the IAM access token as described in [RFC 6750, section 2.1. Authorization Request Header Field](https://tools.ietf.org/html/rfc6750#page-5){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"):

Review the following example:

  1.	Use the HTTP header Authorization
  2.	Prefix the IAM access token with the literal `Bearer: Bearer eyJhbGciOiJSUzI1Ng...`
  3.	Add the prefixed IAM access token to the HTTP header: `Authorization: Bearer eyJhbGciOiJSUzI1Ng...`. When you use the curl command, you can pass this with the parameter -H:

    ```
    curl -H "Authorization: Bearer eyJhbGciOiJSUzI1Ng..."
    ```

  Use the same IAM access token for subsequent IBM Cloud service API calls to achieve the best performance and scalability.
  {: tip}
