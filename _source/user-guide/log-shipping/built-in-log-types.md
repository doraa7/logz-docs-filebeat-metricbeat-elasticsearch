---
layout: article
title: Default parsing
permalink: /user-guide/log-shipping/built-in-log-types.html
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Parse your logs with Logz.io
tags:
  - log-shipping
  - log-types
  - parsing
contributors:
  - shalper
  - schwin007
  - imnotashrimp
  - nshishkin
---

Logz.io automatically parses logs shipped from many platforms, services, containers, servers, and more.

The shipping configuration includes a log **type** parameter that determines which pipeline is used to parse the data. In OpenSearch Dashboards, it is indicated by a field named `type`.

Logz.io offers many pre-built parsing pipelines for a large number of log sources, as shown below. If you need a new pipeline created or want a customized version of an existing pipeline, contact [Logz.io Support](mailto:help@logz.io). Parsing-as-a-service is included in your package and we're happy to offer it.

You can replace the `@timestamp` field by sending it in a different format. The available formats are:

* ISO8601 - `2023-05-21T12:45:10+00:00`.
* UNIX - `1684662310`.
* UNIX_MS - `1684673200471`.

## Built-in log types

This table shows the log types that Logz.io parses automatically.

| Description           | Type                                       | Prebuilt parsing pipeline unless marked |
|-----------------------|--------------------------------------------|
| Alcide kAudit         | `alcide-kaudit` | ✖️ Auto-parsed as part of platform integration. |
| Apache access         | `apache`, `apache_access`, `apache-access` | ✔ |
| Auditd                | `auditd`                                   | ✔ |
| AWS CloudFront        | `cloudfront`                               | ✔ |
| AWS CloudTrail        | `cloudtrail`                               | ✔ |
| AWS ELB               | `elb`                                      | ✔ |
| AWS Fargate           | `fargate`                                  | ✖️ Auto-parsed as part of platform integration. |
| AWS GuardDuty             | `guardduty`                                | ✔ |
| AWS Route 53          | `route_53`                                 | ✔ |
| AWS S3 access         | `S3Access`                                 | ✔ |
| AWS VPC Flow           | `vpcflow`                                  | ✔ |
| AWS WAF         | `awswaf`                                 | ✖️ Auto-parsed as part of platform integration. |
| Checkpoint            | `checkpoint`                               | ✔ |
| Cisco ASA             | `cisco-asa`                                | ✔ |
| Cisco Meraki          | `cisco-meraki`                             | ✔ |
| Crowdstrike           | `crowdstrike`                              | ✔ |
| Docker                | `docker_logs`                              | ✔ |
| Docker Collector Logs | `docker-collector-logs`                    | ✔ |
| Elasticsearch         | `elasticsearch`                            | ✔ |
| Fail2ban              | `fail2ban`                                 | ✔ |
| Falco                 | `falco`                                    | ✔ |
| Fargate                 | `fargate`                                | ✖️ Auto-parsed as part of platform integration. |
| Fortigate             | `fortigate`                               | ✔ |
| GitHub                  | `github`                                     | ✖️ Auto-parsed as part of platform integration. |
| GPFS                  | `gpfs`                                     | ✔ |
| HAProxy Load Balancer              | `haproxy`                                  | ✔ |
| Jenkins               | `jenkins`                                  | ✔ |
| Juniper                  | `juniper`                             | ✔ |
| Kafka                 | `kafka_server`                             | ✔ |
| Kubernetes                 | `k8s`                             | ✖️ Auto-parsed as part of platform integration. |
| Mcafee EPO            | `mcafee_epo`                                      | ✔ |
| Microsoft IIS         | `iis`                                      | ✔ |
| ModSecurity               | `modsecurity`                                  | ✖️ Auto-parsed as part of platform integration. |
| MongoDB               | `mongodb`                                  | ✔ |
| Monit                 | `monit`                                    | ✔ |
| MySQL                 | `mysql`                                    | ✔ |
| MySQL error           | `mysql_error`                              | ✔ |
| MySQL monitor         | `mysql_monitor`                            | ✔ |
| MySQL slow query      | `mysql_slow_query`                         | ✔ |
| Nagios                | `nagios`                                   | ✔ |
| NGINX access          | `nginx`, `nginx_access`, `nginx-access`    | ✔ |
| NGINX error           | `nginx-error`                              | ✔ |
| OpenVAS                 | `openvas`                                    | ✔ |
| OpenVPN                 | `openvpn`                                    | ✔ |
| OSSEC                 | `ossec`                                    | ✔ |
| Trend Micro                 | `trendmicro_deep`                    | ✔ |
| Palo Alto Networks    | `paloalto`                                  | ✔ |
| Performance-tab       | `performance-tab`                                  | ✔ |
| pfSense       | `pfsense`                                  | ✔ |
| Sonicwall                | `sonicwall`                                  | ✔ |
| Sophos Intercept X       | `sophos-ep`                                  | ✖️ Auto-parsed as part of platform integration. |
| Stormshield                | `stormshield`                              | ✔ |
| Sysmon                | `wineventlog`                              | ✔ |
| Windows WinEventLog          | `wineventlog`                             | ✔ |
| Zeek           | `zeek`                              | ✔ |
| Zipkin span           | `zipkinSpan`                             | ✔ |
