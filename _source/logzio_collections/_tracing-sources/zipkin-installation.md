---
title: Send traces from your Zipkin installation to Logz.io
logo:
  logofile: zipkin.png
  orientation: vertical
data-source: Zipkin installation
data-for-product-source: Tracing
description: Send traces from your Zipkin installation to Logz.io
contributors:
  - yyyogev
  - yberlinger
  - doron-bargo
shipping-tags:
  - existing-instrumentation
order: 330
---

<!-- tabContainer:start -->
<div class="branching-container">

* [Overview](#overview)
* [Local host](#local-host)
* [Troubleshooting](#troubleshooting)
{:.branching-tabs}

<!-- tab:start -->
<div id="overview">

Deploy this integration to send traces from your Zipkin installation to Logz.io.

Logz.io recommends that you use OpenTelemetry to gather trace transaction data from your system. Because of its versatility, OpenTelemetry has been widely adopted as the industry standard: OpenTelemetry can be equipped with many additional functionalities, one of which is collecting aggregated trace data. Beyond that, [OpenTelemetry](https://github.com/open-telemetry) is set to be the best production-ready solution going forward.

### Architecture overview

This integration includes:

* Installing the OpenTelemetry collector with Logz.io exporter on your application host
* Configuring the collector to receive traces from your Zipkin installation and send them to Logz.io

On deployment, your Zipkin instrumentation captures spans from your application and forwards them to the collector, which exports the data to your Logz.io account.

</div>
<!-- tab:end -->


<!-- tab:start -->
<div id="local-host">


### Set up your locally hosted Zipkin installation to send traces to Logz.io

**Before you begin, you'll need**:

* An application instrumented with Zipkin
* An active account with Logz.io

<!-- info-box-start:info -->
This integration uses OpenTelemetry Collector Contrib, not the OpenTelemetry Collector Core.
{:.info-box.note}
<!-- info-box-end -->

<div class="tasklist">

##### Download and configure OpenTelemetry collector

Create a dedicated directory on the host of your application and download the [OpenTelemetry collector](https://github.com/open-telemetry/opentelemetry-collector-contrib/releases/tag/v0.70.0) that is relevant to the operating system of your host.


After downloading the collector, create a configuration file `config.yaml` with the following parameters:

```yaml
receivers:
  zipkin:
    endpoint: "0.0.0.0:9411"


exporters:
  logzio/traces:
    account_token: "<<TRACING-SHIPPING-TOKEN>>"
    region: "<<LOGZIO_ACCOUNT_REGION_CODE>>"

processors:
  batch:
  tail_sampling:
    policies:
      [
        {
          name: policy-errors,
          type: status_code,
          status_code: {status_codes: [ERROR]}
        },
        {
          name: policy-slow,
          type: latency,
          latency: {threshold_ms: 1000}
        }, 
        {
          name: policy-random-ok,
          type: probabilistic,
          probabilistic: {sampling_percentage: 10}
        }        
      ]

extensions:
  pprof:
    endpoint: :1777
  zpages:
    endpoint: :55679
  health_check:

service:
  extensions: [health_check, pprof, zpages]
  pipelines:
    traces:
      receivers: [zipkin]
      processors: [batch]
      exporters: [logzio/traces]
```

{% include /tracing-shipping/replace-tracing-token.html %}
{% include /tracing-shipping/tail-sampling.md %}


##### Start the collector

Run the following command:

```shell
<path/to>/otelcontribcol_<VERSION-NAME> --config ./config.yaml
```
* Replace `<path/to>` with the path to the directory where you downloaded the collector.
* Replace `<VERSION-NAME>` with the version name of the collector applicable to your system, e.g. `otelcontribcol_darwin_amd64`.

##### Run the application

Run the application to generate traces.


##### Check Logz.io for your traces

Give your traces some time to get from your system to ours, and then open [Tracing](https://app.logz.io/#/dashboard/jaeger).

</div>

</div>
<!-- tab:end -->

<!-- tab:start -->
<div id="troubleshooting">

{% include /tracing-shipping/otel-troubleshooting.md %}

</div>
<!-- tab:end -->

</div>
<!-- tabContainer:end -->
