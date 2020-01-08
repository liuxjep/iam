---

copyright:

  years: 2015, 2020
lastupdated: "2020-01-08"

keywords: API key, user API keys, IBM Cloud API keys, manage user keys, create API key

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'} 

# Managing user API keys
{: #userapikey}

A federated user or non-federated user can create an API key to use on the CLI or as part of automation to log in as your user identity. You can use the UI or the CLI to manage your API keys by listing your keys, creating keys, updating keys, or deleting keys. To manage the {{site.data.keyword.Bluemix_notm}} API keys that are associated with your user identity, go to **Manage** &gt; **Access (IAM)** &gt; **IBM Cloud API keys**. Then, you can create, edit, or delete API keys. And, for a full list of available CLI commands, see [`ibmcloud iam api-keys`](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_iam#ibmcloud_iam_api_keys).

As a [federated user](/docs/account?topic=account-signup#signup), you can use an API key to log in by using the `IBMCLOUD_API_KEY` environment variable. For more information about using an API key for logging in, see [Logging in with a federated ID](/docs/iam?topic=iam-federated_id#federated_id).
{:shortdesc}

## Creating an API key
{: #create_user_key}
{: help}
{: support}

As an {{site.data.keyword.Bluemix_notm}} user you might want to use an API key when you enable a program or script without distributing your password to the script. A benefit of using an API key can be that a user or organization can create several API Keys for different programs and the API keys can be deleted independently if compromised without interfering with other API keys or even the user. You can create up to 20 API keys.

To create an API key for your user identity in the UI, complete the following steps:

1. Go to **Manage** &gt; **Access (IAM)** &gt; **IBM Cloud API keys**.
2. Click **Create an {{site.data.keyword.Bluemix_notm}} API key**.
3. Enter a name and description for your API key.
4. Click **Create**.
5. Then, click **Show** to display the API key. Or, click **Copy** to copy and save it for later, or click **Download**.

For security reasons, the API key is only available to be copied or downloaded at the time of creation. If the API key is lost, you must create a new API key.
{: tip}

To create an API key by using the CLI, use the following command:

1. Enter `ibmcloud iam api-key-create NAME [-d DESCRIPTION] [-f, --file FILE]` in your command prompt, and specify a name, description, and file for saving your key. See the following example:

```
ibmcloud iam api-key-create MyKey -d "this is my API key" --file key_file
```


## Updating an API key
{: #update_user_key}

If you want to change the name or the description of an API key, complete the following steps in the UI or CLI.

To edit an API key, complete the following steps:

1. Go to **Manage** &gt; **Access (IAM)** &gt; **IBM Cloud API keys**.
2. Identify the row of the API key that you want to update, and select **Edit** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.
3. Update the information for your API key.
4. Click **Apply**.

To edit an API key by using the CLI, enter the following command:

1. Enter `ibmcloud iam api-key-update NAME [-n NAME] [-d DESCRIPTION]` in your command prompt, specifying the old name, new name, and new description for the key. For example:

```
ibmcloud iam api-key-update MyCurrentName -n MyNewName -d "the new description of my key"
```

## Locking an API key
{: #lock_user_key}

For platform API keys that represent your user identity you can prevent the API key from being deleted by locking it. A locked API key is indicated by the ![Locked icon](images/locked.svg "Locked") icon. You can lock and unlock your API key by using the UI or CLI.

### Locking and unlocking an API key from the UI
{: #lockui}

1. Go to **Manage** &gt; **Access (IAM)** &gt; **IBM Cloud API keys**.
2. Identify the row of the API key that you want to lock, and select **Lock** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.

You can unlock your API key at any time to update or remove the API key from your account. Select the API key from the table that you want to unlock and select **Unlock** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.
{: tip}

### Locking and unlocking an API key by using the CLI
{: #lockcli}

To lock an API key, use the following command:

```
ibmcloud iam api-key-lock (NAME|UUID) [-f, --force]
```

<strong>Prerequisites</strong>:  Endpoint, Login

<strong>Command options</strong>:
<dl>
<dt>NAME (required)</dt>
<dd>Name of the API key to be locked, exclusive with UUID.</dd>
<dt>UUID (required)</dt>
<dd>UUID of the API key to be locked, exclusive with NAME.</dd>
<dt>-f, --force</dt>
<dd>Forces lock without confirmation.</dd>
</dl>

<strong>Example</strong>:

Lock API key `test-api-key`

```
ibmcloud iam api-key-lock test-api-key
```

To unlock an API key, run the following command:

```
ibmcloud iam api-key-unlock (NAME|UUID) [-f, --force]
```

<strong>Prerequisites</strong>:  Endpoint, Login

<strong>Command options</strong>:
<dl>
<dt>NAME (required)</dt>
<dd>Name of the API key to be unlocked, exclusive with UUID.</dd>
<dt>UUID (required)</dt>
<dd>UUID of the API key to be unlocked, exclusive with NAME.</dd>
<dt>-f, --force</dt>
<dd>Forces unlock without confirmation.</dd>
</dl>

<strong>Example</strong>:

Unlock API key `test-api-key`

```
ibmcloud iam api-key-unlock test-api-key
```


## Deleting an API key
{: #delete_user_key}

If you are using a key rotation strategy, you might want to delete an older key and replace it with a new key.

To delete an API key, complete the following steps:

1. Go to **Manage** &gt; **Access (IAM)** &gt; **IBM Cloud API keys**.
2. Identify the row of the API key that you want to delete, and select **Delete** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.
3. Then, confirm the deletion by clicking **Delete**.

To delete an API key by using the CLI:
1. Enter `ibmcloud iam api-key-delete NAME` in your command prompt, specifying the name of the key to delete.
