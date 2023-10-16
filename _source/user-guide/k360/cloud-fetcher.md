---
layout: article
title: Configure Azure Native Integration
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Step by step guide to configuring Azure native integration
permalink: /user-guide/azure-native-integration.html
flags:
tags:
  - cloud
  - cloud fetcher
  - Azure Native Integration
  - ship data
  - Azure
contributors:
  - hidan
---


Azure Native Integration offers a fast and efficient way to sync your Azure data with Logz.io, providing visibility and allowing you to monitor and troubleshoot your environments. With Azure Native Integration, you can monitor the performance and health of your systems in real-time, and quickly identify the root cause of issues and problems.

Azure may **charge additional fees** for using this integration. [Read more about Azure API costs](https://azure.microsoft.com/en-us/pricing/details/api-management/).
{:.info-box.important}

* [Set up Azure Native Integration](/user-guide/azure-native-integration.html#set-up-azure-native-integration)
  * [Collect logs with Azure Native Integration](/user-guide/azure-native-integration.html#collect-logs-with-azure-native-integration)
* [Set up Logz.io's Azure Native Integration](/user-guide/azure-native-integration.html#set-up-logzios-azure-native-integration)


#### Set up Azure Native Integration

<div class="tasklist">

##### Create a new app in Azure

Enter your Azure portal and navigate to **App registrations > New registration**. 

Give your app a name, choose Accounts in this organizational directory only (**Single tenant**), and click the Register button.

![create an app](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/register-azure.png)

##### Create a certificate

In your main app screen, click on **Add a certificate or secret**. 

![certificate or secret](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/azure-certificate.png)

Next, create a **New client secret**. Give it a description and choose the expiration date, such as the 730 days option. Click **Add** to create the secret.

<!-- ![add a secret](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/add-client-secret.png)-->

Copy your secret's **Value** and save if for later use. This is needed to complete the setup process with Logz.io.

Client secret values **cannot be viewed except immediately after creation**. Be sure to save the secret when created before leaving the page. If you didn't keep the value, create a new client secret to continue the setup process.
{:.info-box.important}

![secret value](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/secret-value-copy.png)

##### Assign a role

Navigate to **Subscriptions** and choose the relevant Azure subscription. Inside, click on **Access control (IAM) > Role assignments tab**. 

![assign role](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/role-assignment.png)

Click on **Add** and choose **Add role assignment**.

![role assignment](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/add-role-dropdown.png)

Search for the **Monitoring reader** role, select it, and click next. 

![monitor reader](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/monitor-role.png)

Ensure that the **User, group, or service principal** option is checked in the Members tab, and click on **+ Select members**.

![add role from list](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/add-role-from-list.png)

Search for the name of the app you created and select it. Click **Review + assign** to confirm. Click on **Review + assign** again to apply the role.

##### _Optional_ Collect logs with Azure Native Integration

Azure Native Integration collects metrics data by default. If you wish to collect and monitor your logs, you'll need to:

* 1. [Create a workspace in Azure](https://learn.microsoft.com/en-us/azure/machine-learning/quickstart-create-resources?view=azureml-api-2)
* 2. Configure your logs and send them to the relevant workspace

You can create a workspace and configure your logs in Azure in several methods, according to your Azure configuration.

For example, if you have a Virtual Machine you can navigate to **Virtual Machine** > **Diagnostic settings**, choose the storage account you want to enable diagnostics for and click **Add diagnostic settings**. 

Next, choose which log categories to monitor and set up the Destination details to Send to Log Analytics workspace.

Once you connect your Azure Native Integration with Logz.io, it'll have access to all logs inside the workspace, which will be monitored on your Logz.io dashboard. 

![configure logs in Azure](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/confugure-azure-logs.png)


##### Send your details to Logz.io

To connect your Azure Native Integration with Logz.io you'll need to send the following information:

* **Client secret value** - that you created and copied in the [Create a certificate](/user-guide/cloud-fetcher.html#create-a-certificate) section.

Navigate to App registration and click on the app you created. There, you'll be able to find the following information:

* **Application (client) ID**
* **Directory (tenant) ID**

![app ids](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/app-id-for-logz.png)

Next, navigate to Subscriptions and copy the **Subscription ID**:

![subscription id](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/subscription-id.png)

And lastly, navigate to **Resource groups** and copy the group’s name associated with the app you created. _This step is optional._

![resource group](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/resource-group-copy.png)


</div>

## Set up Logz.io's Azure Native Integration

Once your Azure app is ready, navigate to Logz.io to continue the setup process.


<div class="tasklist">

##### Setup Azure Native Integration

Open **[Logz.io > Send data > Telemetry Collector](https://app.logz.io/#/dashboard/send-your-data/agent/new)** and Choose Azure.

![Azure telemetry collector](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/choose-azure-cloud.png)

##### Enter your credentials

Take the credentials you've copied from your Azure app and enter the required values:

* **Tenant ID** - Your Azure app's directory ID
* **Client ID** - Your Azure app's application ID
* **Client Secret** - The value you've copied in the [Create a certificate](/user-guide/cloud-fetcher.html#create-a-certificate) section
* **Subscription** - Your Azure app's subscription ID
* *Optional* - **Resource group name** - The name of the group that's associated with the Azure app you created
* _Optional_ - **Tags** - You can add tags associated with the sent data for easier analysis and identification

Next, select the resource type you'd like to send. You can select **All services** to send all resource types of the project or manually add the relevant resources from the drop-down list.

Click **Next** to continue.

![Enter Azure details](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/configure-azure-fetcher.png)

##### Finish setting up your collector

Finilaze your collector by giving it a meaningful name, adding a description, and selecting which Metrics account you'd like to use. If you don't have an active Metrics account, it will be created automatically.

Click **Generate collector** to continue.

##### Activate and run the collector

To get started with Azure Native Integration, toggle the **Enable Connection** on. You might have to wait a few minutes to see your data.

![Toggle integration](https://dytvr9ot2sszz.cloudfront.net/logz-docs/fetcher/toggle-fetcher.png)

If you encounter an error and can't enable the connection, click **Advanced settings** to return to the configuration screen and verify the values you've entered are correct.

##### Explore Logz.io

Once your Azure Native Integration is running, you can explore and analyze your data through Logz.io's dashboards.

</div>
