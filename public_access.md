---

copyright:

  years: 2019

lastupdated: "2020-01-10"

keywords: public access, anonymous access, users, service IDs, public access group, enable, disable, manage, IAM

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Managing public access to resources
{: #public}

By default, all users, both authenticated and unauthenticated, and service IDs in an account are members of the Public Access group. You can give all members of the group access to specific resources by defining those resources in a policy. In some cases, however, you might want to prevent public access to the resources, which you control by disabling public access at the account level. 
{:shortdesc}

To manage public access, you must be an administrator of the IAM Access Groups service in the account.

## Assigning public access to resources
{: #public_policy}

When public access is enabled in the account, you can create a policy to define the resources that all members of the Public Access group can access. To create a policy, you must have administrator access on the resource. 

As an example, the following section describes how to assign public access to an {{site.data.keyword.cos_full}} bucket that's named `mybucket123`. 

### Assigning access in the console
{: #public-access-console}

1. From the console menu bar, click **Manage** > **Access (IAM)**, and select **Access groups**.
2. Click the name of the public access group > **Assign access**.  
3. Select **{{site.data.keyword.cos_short}}** from the **Services** list.
4. Select the specific instance from the **Service instance** list.
5. Enter `bucket` for the resource type.
6. Enter `mybucket123` for the resource ID.
7. Select the service access role, and click **Assign**. 
8. Confirm that you want to assign the public access policy to the resource, and click **Assign**.

### Assigning access by using the CLI
{: #public-access-cli}

To assign access for the Public Access group, run the **`ibmcloud iam access-group-policy-create`** command. In the command example, the policy details are specified in a JSON file. See [Assigning access by using the API](#public-access-api) for an example of what to include in the JSON file.

```
$ ibmcloud iam access-group-policy Public Access -f @policy.json
```

For details about the command options, see [`ibmcloud iam access-group-policy-create`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_iam#ibmcloud_iam_access_group_policy_create).

### Assigning access by using the API
{: #public-access-api}
 
The following request example creates a policy for the Public Access group. 

```
curl -X POST \
'https://iam.cloud.ibm.com/v1/policies' \
-H 'Authorization: $TOKEN' \
-H 'Content-Type: application/json' \
-d '{
  "type": "access",
  "subjects": [
    {
      "attributes": [
        {
          "name": "access_group_id",
          "value": "AccessGroupId-PublicAccess"
        }
      ]
    }
  ],
  "roles":[
    {
      "role_id": "crn:v1:bluemix:public:iam::::role:Administrator"
    }
  ],
  "resources":[
    {
      "attributes": [
        {
          "name": "accountId",
          "value": "$ACCOUNT_ID"
        },
        {
          "name": "serviceName",
          "value": "$SERVICE_NAME"
        },
      ]
    }
  ]
}'
```
{: codeblock}

For more information, see [Create a policy](https://cloud.ibm.com/apidocs/iam-policy-management#create-a-policy){: external}.

## Disabling public access to resources
{: #disable-public-access}

When you disable public access, all existing policies for the Public Access group are deleted, which means all group members no longer have access to IAM-enabled services. Also, you can't create or modify any policies for public access. 

### Disabling access in the console
{: #disable-public-ui}

To disable public access for the account, go to **Manage** > **Access (IAM)** > **Settings**, and set the Public access setting to **Disable public access**.

### Disabling access by using the API
{: #disable-public-api}

The following request example disables public access for the account. 

```
curl -X PATCH \
'https://iam.cloud.ibm.com/v2/groups/settings?account_id=<account_id>' \
-H 'Authorization: $TOKEN' \
-H 'Content-Type: application/json' \
-d '{
  "public_access_enabled": false
}'
```
{: codeblock}

For more information, see [Update account settings](https://cloud.ibm.com/apidocs/iam-access-groups#update-account-settings){: external}.

