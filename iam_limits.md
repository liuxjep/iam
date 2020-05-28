---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: maximum limits, limits, maximum policies

subcollection: iam

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# {{site.data.keyword.Bluemix_notm}} IAM limits
{: #iam_limits}

The following table lists the maximum limits for {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) resources. These limits apply to any user who can create {{site.data.keyword.Bluemix_notm}} IAM resources. If a limit is exceeded, you receive an exception and are not allowed to create any new resources beyond that limit.
{:shortdesc}

| Resource                               | Max  |
|----------------------------------------|------|
| Access groups per account              | 500  |
| Access groups per user                 | 50   |
| Service IDs per account                | 2000 |
| API Keys per identity                  | 20   |
| Dynamic rules per access group         | 5    |
| Policies per account                   | 2010 |
| Policies per subject within an account | 500  |
| Custom roles per account               | 40   |
{:caption="Table 1. IAM Account Limits" caption-side="top"}

A maximum of 1,000 policies and service to service authorizations within one account is recommended to ensure optimal performance within your account. For more information about limiting the number of policies in your account, see the [Best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup).
{: tip}

## Checking the number of policies in an account 
{: #number-policies}

If you aren't sure how many policies are in your account, and you want to ensure that you avoid reaching the limit, you can check how many policies are in your account and work to reduce policies as you approach the limit. You must be the account owner or administrator for all account management services to check how many policies exist in the account.

### Getting the total number of policies per account
{:# total-number-policies}

To get the total number of policies per account, you can use the [IAM Policy Management API](/apidocs/iam-policy-management#get-policies-by-attributes):

1. Log in to [IBM Cloud CLI](/docs/cli?topic=cli-getting-started):
2. Generate your IAM access token: 
    ```
       ibmcloud iam oauth-tokens
    ```
3. Enter the following `curl` command to get a total number of policies in one account. You might want to install `jq` to format the JSON, which is used in the folling examples: 
    ```
       curl --location --request GET "https://iam.cloud.ibm.com/v1/policies?account_id=<account_id>" \
         --header "Content-Type: application/json" \
         --header "Authorization: <IAM TOKEN>" | jq -r .policies | jq '. | length'
    ```
In the following example output the last line displays the total number of policies:
    ```
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
      100  2919  100  2919    0     0   3918      0 --:--:-- --:--:-- --:--:--  3912
      351
    ```

### Getting the total of a specific type of policies per account
{: #total-policies-by-type}

To get the total number of policies for a specific subject, you can use the [IBM Cloud CLI](/docs/cli?topic=cli-getting-started):

Log in, and select your account to run the appropiate CLI command. You might want to install `jq` to format JSON in the CLI output.
  
* To get count of policies for a service id:
    ```
       ibmcloud iam service-policies <service-id> -f --output JSON | jq '. | length'
    ```
* To get count of policies for a username(email):
    ```
       ibmcloud iam user-policies <username> -f --output JSON | jq '. | length'
    ```
* To get count of policies for an access group id:
    ```
    ibmcloud iam access-group-policies <access-group> -f --output JSON | jq '. | length'
    ```

## Requesting a policy limit increase
{: #limit-increase}

You can request a limit increase for the total number of policies that are allowed in the account only if the following criteria is met: 

* You must be the account owner or an administrator on all account management services.
* Access groups are currently used to limit the overall number of policies in the account.
* Use policies for resources grouped by resource group.
* You have taken efforts to clean up and reduce the number of policies in the account.

If you meet all of the listed criteria, you can request a policy limit increase by submitting a support case in the [console](https://{DomainName}/unifiedsupport/cases/add){: external}. In the case, provide all of the following information. Each piece of information is required for processing and approval of your request.

* Case title of `Request to increase account policy limit`
* The use case for the extra policies
* Information on all efforts taken to follow the [Best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup) to reduce the number of policies on the account
* Account ID
* Note how many extra policies in the account are required
* If you are requesting an increase per subject, note how many extra policies per subject are required
* An estimate of when you expect or plan to create extra policies

You are notified of the update to your policy limits through the case.
{: note}

