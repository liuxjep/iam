---

copyright:
  years: 2018, 2020
lastupdated: "2020-02-04"

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
