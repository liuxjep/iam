---

copyright:

  years: 2018, 2020

lastupdated: "2020-04-08"

keywords: event tracking, IAM events, monitoring

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:deprecated: .deprecated}

# Auditing events for IAM
{: #tracking}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full}} service to track how users and applications interact with {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 
{:shortdesc}

You must create an instance of the {{site.data.keyword.at_short}} service in the `eu-de` region to start tracking IAM events. When you create the instance, you can track the following events:

* Managing access groups by creating and deleting groups or adding and removing users
* Creating, updating, or deleting service IDs
* Creating, updating, or deleting API keys
* Creating, updating, or deleting access policies
* Logging in to {{site.data.keyword.Bluemix_notm}} by using an API key, authorization code, passcode, password, or an API key associated with a service ID

To get started monitoring your user's actions, see [{{site.data.keyword.at_short}}](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started#getting-started). For more information about each of the event areas that you can track, see [IAM events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-at_events_iam).

As of 9 May 2019 the {{site.data.keyword.cloudaccesstraillong}} service is deprecated. You must create an instance of the {{site.data.keyword.at_short}} in your account to continue tracking IAM events. For more information, see [Deprecation of the IBM Cloud Activity Tracker service](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
{: deprecated}
