---
layout: article
title: Amazon VPN
permalink: /user-guide/infrastructure-monitoring/metrics-dashboards/amazon-vpn.html 
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: View and analyze metrics with Amazon VPN
flags:
  logzio-plan: pro
tags:
  - metrics integrations
contributors:
  - nshishkin
---


This dashboard provides an interface to view and analyze metrics from your Amazon VPN.

| Metric visualization | Metric name                                                       | Description                                                                                                   |
| -------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| VPN State            | aws\_vpn\_tunnel\_state\_sum                                      | The state of the tunnels.                                                                                     |
| VPN Data In Vs. Out  | aws\_vpn\_tunnel\_data\_in\_sum, aws\_vpn\_tunnel\_data\_out\_sum | The bytes received and sent on the AWS side of the connection through the VPN tunnel from a customer gateway. |
