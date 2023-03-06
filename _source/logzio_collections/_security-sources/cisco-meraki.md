---
title: Ship Cisco Meraki logs
logo:
  logofile: cisco-meraki-logo.png
  orientation: horizontal
data-source: Cisco Meraki
data-for-product-source: Cloud SIEM
templates: ["network-device-filebeat"]
contributors:
  - shalper
  - dorisnaaman
shipping-tags:
  - firewalls
  - endpoint-security
order: 550
---
Cisco Meraki is a centralized management service that allows users to manage all of their Meraki network devices via a single simple and secure platform. 

#### Configuration

**Before you begin, you'll need**:

* [Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-installation.html)
* Root access

<div class="tasklist">

##### Configure Cisco Meraki logging

Configure your Cisco Meraki server to write all logs to a single file and to send logs to your Filebeat server.
Make sure you meet this configuration:

* Log format: syslog
* Send over: UDP
* IP address: Filebeat server IP address
* Port 1514


See [Cisco Meraki docs](https://documentation.meraki.com/zGeneral_Administration/Monitoring_and_Reporting/Syslog_Server_Overview_and_Configuration) for more information
on configuring your Syslog Server.

{% include log-shipping/certificate.md %}

##### Configure Filebeat

In the Filebeat configuration file (/etc/filebeat/filebeat.yml) add UDP traffic as an input
and Logz.io as an output.

{% include log-shipping/filebeat-input-extension.md %}


```yaml
# ...
filebeat.inputs:
- type: udp
  max_message_size: 10MiB
  host: "0.0.0.0:1514"

  fields:
    logzio_codec: plain

    # Your Logz.io account token. You can find your token at
    #  https://app.logz.io/#/dashboard/settings/manage-accounts
    token: <<LOG-SHIPPING-TOKEN>>
    type: cisco-meraki
  fields_under_root: true
  encoding: utf-8
  ignore_older: 3h 
  
  # ... For Filebeat 7 only ...
filebeat.registry.path: /var/lib/filebeat
processors:
- rename:
    fields:
    - from: "agent"
      to: "filebeat_agent"
    ignore_missing: true
- rename:
    fields:
    - from: "log.file.path"
      to: "source"
    ignore_missing: true
    
# ...
output.logstash:
  hosts: ["<<LISTENER-HOST>>:5015"]
  ssl:
    certificate_authorities: ['/etc/pki/tls/certs/COMODORSADomainValidationSecureServerCA.crt']
```

{% include /general-shipping/replace-placeholders.html %}


<!-- info-box-start:info -->
One last validation - make sure Logz.io is the only output and appears only once.
If the file has other outputs, remove them.
{:.info-box.note}
<!-- info-box-end -->


##### Start Filebeat


[Start or restart Filebeat](https://www.elastic.co/guide/en/beats/filebeat/master/filebeat-starting.html) for the changes to take effect.


##### Check Logz.io for your logs

Give your logs some time to get from your system to ours, and then open [Open Search Dashboards](https://app.logz.io/#/dashboard/osd).

If you still don't see your logs, see [Filebeat troubleshooting](https://docs.logz.io/shipping/log-sources/filebeat.html#troubleshooting).

</div>
