# Plugins

### Overview <a href="#overview" id="overview"></a>

This page explains the jobs to be run to build and deploy plugins. In order to do so, log into Jenkins and execute the instructions as per the sequence provided on this page.

### Build <a href="#build" id="build"></a>

Switch to the `Build/Plugins` folder and run all jobs. Ensure all ArtifactUpload jobs are sucessful after the build. For the value of the **github\_release\_tag**, refer to [Current Release Tags and Jenkins Jobs Reference](broken-reference)

#### Prerequisites Before Deployment <a href="#prerequisites-before-deployment" id="prerequisites-before-deployment"></a>

**Create Containers**

Create containers in Azure blob. Use the following commands to create initial placeholder containers:

```
  az storage blob upload-batch --destination container_name/collection-editor --source some_folder --account-name storage_account_name --account-key account_key

az storage blob upload-batch --destination container_name/generic-editor --source some_folder --account-name storage_account_name --account-key account_key

az storage blob upload-batch --destination container_name/content-editor --source some_folder --account-name storage_account_name --account-key account_key

az storage blob upload-batch --destination container_name/v3/preview --source some_folder --account-name storage_account_name --account-key account_key

```

> **Note:**
>
> 1. The commands only create the required directories in Azure blob. The deployment script always tries to delete the folders before deploying new contents. Hence, if these folders are not available during the first run, the deployment script fails.
> 2. You can upload any content in the blob for the first run. Azure does not allow you to create emtpy folders. Hence, add a file in a folder named _dummy_. The commands mentioned create the required directories.
> 3. The **container\_name** container must be publicly accessible.

**Upload Base Plugin**

Upload the initial set of plugins (base plugins) to your publicly accessible Azure container.

> **Note:** The name of the Azure container must be same as the **container\_name** mentioned in the section on creating containers.

You can download the initial Plugins from [here](https://sunbirdpublic.blob.core.windows.net/installation/content-plugins.zip)

Unzip the contents and the directory **content-plugins** is available. Run the following command from the directory where the zip was extracted.

```
  az storage blob upload-batch --destination container_name/content-plugins --source content-plugins --account-name account_name --account-key account_key

```

### Deploy <a href="#deploy" id="deploy"></a>

Switch to `Deploy/<env>/Plugins` in your jenkins machine and run the jobs in the following sequence:

1.ContentPlugins\
2.ContentPlayer\
3.CollectionEditor\
4.ContentEditor\
5.GenericEditor

After the plugins are deployed, you get URL’s for the editors zip file. Sample URLs will be similar to the following:

https://.blob.core.windows.net//artefacts/editor/generic-editor-iframe-2.5.0.zip

https://.blob.core.windows.net//artefacts/editor/collection-editor-iframe-2.5.0.zip

https://.blob.core.windows.net//artefacts/editor/content-editor-iframe-2.5.0.zip

You will need to use these 3 URL’s when building Player service.
