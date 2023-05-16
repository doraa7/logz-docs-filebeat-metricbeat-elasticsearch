---
layout: article
title: Using Inspect feature on OpenSearch Dashboards UI
permalink: /api/cookbook/inspect.html
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: Using OpenSearch Dashboards UI Inspect
flags:
  logzio-plan: pro
tags:
  - api
  - api-cookbook
contributors:
  - nshishkin
  - hidan
---

If you want to search logs using our [Search API](https://docs.logz.io/api/#operation/search), an easy way to construct your query is to use the OpenSearch Dashboards UI.


<div class="tasklist">

##### Construct the search query

Enter the search query into the search bar on your OpenSearch Dashboards UI.

For example, you can filter by the log type: `type:payment`. This search query will retrieve all log entries that match the log type.

![Search](https://dytvr9ot2sszz.cloudfront.net/logz-docs/api-cookbook/search-api.png)



##### Navigate to the Inspect window

Select **Inspect** to open the inspection window.

In the inspection window, select **Request**.

![request](https://dytvr9ot2sszz.cloudfront.net/logz-docs/api-cookbook/inspect-osd.png)


##### Copy the query object

The `query` object of the JSON file displayed, contains the query that you can use in your request via our [Search API](https://docs.logz.io/api/#operation/search).

![JSON object](https://dytvr9ot2sszz.cloudfront.net/logz-docs/api-cookbook/query-osd.png)



</div>
