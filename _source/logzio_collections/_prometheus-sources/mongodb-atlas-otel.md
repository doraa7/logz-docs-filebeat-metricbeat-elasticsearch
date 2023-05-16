---
title: Ship MongoDB Atlas metrics
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Ship MongoDB Atlas metrics to Logz.io
logo:
  logofile: mongoatlas-logo.png
  orientation: vertical
data-source: MongoDB Atlas
data-for-product-source: Metrics
templates: ["docker"]
contributors:
  - nshishkin
shipping-tags:  
  - prometheus
order: 800
---

MongoDB Atlas is a fully-managed cloud database that handles deploying, managing and healing deployments on its cloud service provider.  

Deploy this integration to send your MongoDB Atlas metric to your Logz.io account using OpenTelemetry collector.


#### Deploying the integration

**Before you begin, you'll need**:

* A MongoDB Atlas project
* Private and public keys created for your MongoDB Atlas [organization](https://docs.atlas.mongodb.com/tutorial/configure-api-access/organization/create-one-api-key/) or the [project](https://docs.atlas.mongodb.com/tutorial/configure-api-access/project/create-one-api-key/) to send the data from.
* An active account with Logz.io

<div class="tasklist">

##### Download and configure OpenTelemetry collector

Create a dedicated directory on your host and download the [OpenTelemetry collector](https://github.com/open-telemetry/opentelemetry-collector/releases/tag/v0.60.0) that is relevant to the operating system of your host.

After downloading the collector, create a configuration file `config.yaml` with the following parameters:

```yaml
receivers:
  mongodbatlas:
    public_key: <<YOUR-MONGODB-ATLAS-PUBLIC-KEY>>
    private_key: <<YOUR-MONGODB-ATLAS-PRIVATE-KEY>>

exporters:
  logging:
  prometheusremotewrite:
    endpoint: https://<<LISTENER-HOST>>:8053
    headers:
      Authorization: Bearer <<PROMETHEUS-METRICS-SHIPPING-TOKEN>>

processors:
  batch:

extensions:
  pprof:
    endpoint: :1777
  zpages:
    endpoint: :55679
  health_check:

service:
  extensions: [health_check, pprof, zpages]
  pipelines:
    metrics:
      receivers: [mongodbatlas]
      processors: [batch]
      exporters: [logging, prometheusremotewrite]
```

{% include general-shipping/replace-placeholders-prometheus.html %}
* Replace `<<YOUR-MONGODB-ATLAS-PUBLIC-KEY>>` with the public key to your MongoDB Atlas organization or project.
* Replace `<<YOUR-MONGODB-ATLAS-PRIVATE-KEY>>` with the private key to your MongoDB Atlas organization or project.

##### Start the collector

Run the following command:

```shell
<path/to>/otelcol-contrib --config ./config.yaml
```

* Replace `<path/to>` with the path to the directory where you downloaded the collector.

##### Check Logz.io for your metrics

Give your data some time to get from your system to ours, then log in to your Logz.io Metrics account, and open [the Logz.io Metrics tab](https://app.logz.io/#/dashboard/metrics/).


</div>
