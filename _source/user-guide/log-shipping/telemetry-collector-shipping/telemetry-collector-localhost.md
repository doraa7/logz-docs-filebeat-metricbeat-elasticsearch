---
layout: article
title: Send Localhost data with Telemetry Collector
permalink: /user-guide/log-shipping/telemetry-collector-localhost.html
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Send your Localhost data with Logz.io's Telemetry Collector
tags:
  - log-shipping
contributors:
  - hidan
---

Telemetry Collector is currently **available in all regions** except for Japan and Australia. If you're located in these regions, you can use **[Logz.io’s data shippers](https://app.logz.io/#/dashboard/send-your-data/collection?tag=all&collection=all)** to send your data.
{:.info-box.note}

To start sending Localhost data through the Telemetry Collector, Log into your Logz.io account, navigate to [Send your data](https://app.logz.io/#/dashboard/send-your-data), and click on **Start collecting**.


![Start collecting button](https://dytvr9ot2sszz.cloudfront.net/logz-docs/telemetry-agent/send-data-collector.png)

<div class="tasklist">

##### Select platform

Select the Localhost platform and the relevant sub-type through which you want to send your data.

![Localhost select platform](https://dytvr9ot2sszz.cloudfront.net/logz-docs/telemetry-agent/tc-select-localhost.png)

##### Select data sources

Enter the full path location of your log folders from your machine. You can add multiple log folders to monitor by clicking on the **Add a folder** option.

The Telemetry Collector can also collect metrics data from your logs.

![Select folder collector](https://dytvr9ot2sszz.cloudfront.net/logz-docs/telemetry-agent/log-location.png)

##### Define your collector

Choose a name and write a description to help identify the collector. 

Under **Accounts**, you can review the Logs and Metrics accounts to which the Telemetry Collector will send the data. If you don’t have an existing account, one will be created for you.

Click **Generate snippet** to continue.

![Define collector](https://dytvr9ot2sszz.cloudfront.net/logz-docs/telemetry-agent/define-collector-localhost.png)

Next, review your collector. The Summary, located on the left side of the screen, includes all of the data in the collector.

##### Run the Telemetry Collector

Copy the code snippet and run it on your end:

* **Mac** users - Run the snippet in your terminal.
* **Windows** users - Run the snippet in your PowerShell x64 **as Administrator** (Note that PowerShell x86 and PowerShell ISE are currently not supported).

Some platforms might require additional details, such as admin privileges or passwords, to complete the installation. These details are not sent to or stored by Logz.io.

![Review collector](https://dytvr9ot2sszz.cloudfront.net/logz-docs/telemetry-agent/collector-localhost-finish.png)

##### Collect data

That’s it! It might take a while for the Telemetry Collector to get up and running, after which you’ll be able to view your logs or metrics and get full observability into your system.

</div>

If you encounter issues in installing or running your Telemetry Collector, [contact Logz.io's Support team](mailto:help@logz.io).


#### Manage and remove a Telemetry Collector:

To manage a Localhost Telemetry Collector on your **Mac** machine, you can use the following commands:

| **Collector Binary:** || `/opt/logzio-otel-collector/otelcol-logzio-darwin_amd64` |
| **Collector Config:** || `/opt/logzio-otel-collector/otel_config.yaml` |
| **Start Service Command:** || `sudo launchctl load /Library/LaunchDaemons/com.logzio.OTELCollector.plist` |
| **Stop Service Command:** || `sudo launchctl unload /Library/LaunchDaemons/com.logzio.OTELCollector.plist` |
| **Show Service Command:** || `sudo launchctl list | grep com.logzio.OTELCollector` |
| **Show Logs Command:** || `sudo tail -F /opt/logzio-otel-collector/logzio_otel_collector.log` |


To manage a Localhost Telemetry Collector on your **Windows** machine, you can use the following commands:

| **Collector Binary:** | `C:\Users\LEKO\AppData\Roaming\LogzioOTELCollector\otelcol-logzio-windows_amd64.exe` |
| **Collector Config:** | `C:\Users\LEKO\AppData\Roaming\LogzioOTELCollector\otel_config.yaml` |
| **Start Service Command:** | `Start-Service -Name LogzioOTELCollector` |
| **Stop Service Command:** | `Stop-Service -Name LogzioOTELCollector` |
| **Show Service Command:** | `Get-Service -Name LogzioOTELCollector` |
| **Show Logs Command:** | `eventvwr.msc ('Windows Logs'->'Application' all logs with source 'LogzioOTELCollector')` |
| **Kill Service Command** | `sc.exe DELETE LogzioOTELCollector` |

If you have additional questions about managing your Telemetry Collector, [contact Logz.io's Support team](mailto:help@logz.io).


##### Additional resources

* [View Telemetry Collector on GitHub](https://github.com/logzio/logzio-agent-manifest)