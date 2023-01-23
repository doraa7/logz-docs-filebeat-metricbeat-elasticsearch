---
layout: article
title: Apache Cassandra
permalink: /user-guide/infrastructure-monitoring/metrics-dashboards/apache-cassandra.html 
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: View and analyze metrics with Apache Cassandra
flags:
  logzio-plan: pro
tags:
  - metrics integrations
contributors:
  - nshishkin
---


This dashboard provides an interface to view and analyze metrics from your Apache Cassandra databases.

| Metric visualization                        | Metric name                                                                                                                         | Description                                                                                             |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Client Read Average Duration                | cassandra\_ClientRequest\_Latency\_Mean                                                                                             | Mean of read operations since server start.                                    |
| Client Write Average Duration   | cassandra\_ClientRequest\_Latency\_Mean                                                                                             | Mean of write operations since server start.                                                    |
| Pending Compactions                         | cassandra\_Compaction\_PendingTasks\_Value                                                                                          | Total value of compaction tasks in the queue                                                            |
| Thread Pool Blocked Task       | cassandra\_ThreadPools\_CurrentlyBlockedTasks\_Count                                                                                | Tasks that are currently blocked from processing                                                        |
| JVM Heap Usage                              | java\_Memory\_HeapMemoryUsage\_used, java\_Memory\_HeapMemoryUsage\_max                                                             | Heap memory used in relation to the maximum heap memory.                                                |
| Unavailable Exceptions            | cassandra\_ClientRequest\_Unavailables\_Count                                                                                       | Requests for which the required nodes were unavailable                                                  |
| Read Requests                      | cassandra\_ClientRequest\_Latency\_Count                                                                                            | Read response time.                                                                                     |
| Write Requests                 | cassandra\_ClientRequest\_Latency\_Count                                                                                            | Write response time.                                                                                    |
| Read Latency (99th%)         | cassandra\_ClientRequest\_Latency\_99thPercentile                                                                                   | 99th percentile of Cassandra transactional read latency                                                 |
| Write Latency (99th%)             | cassandra\_ClientRequest\_Latency\_99thPercentile                                                                                   | 99th percentile of Cassandra transactional write latency                                                |
| Cache Hit Rate                 | cassandra\_Cache\_HitRate\_Value                                                                                                    | Rate of the number of cache hits to the number of lookups                                               |
| Occupied Cache Size                 | cassandra\_Cache\_Size\_Value                                                                                                       | Total size of occupied cache                                                                            |
| Pending Compactions Tasks           | cassandra\_Compaction\_PendingTasks\_Value                                                                                          | Number of compactions tasks in the queue.                                                               |
| Completed Compactions Tasks    | cassandra\_Compaction\_CompletedTasks\_Value                                                                                        | Number of compactions tasks completed.                                                                  |
| Bytes Compacted                | cassandra\_Compaction\_BytesCompacted\_Count                                                                                        | Total number of bytes compacted since server \[re\]start.                                               |
| SSTable Accessed Per Read         | cassandra\_ColumnFamily\_SSTablesPerReadHistogram\_99thPercentile                                                                   | 99th percentile of the Histogram of the number of sstable data files accessed per single partition read |
| Disk Usage                        | cassandra\_ColumnFamily\_LiveDiskSpaceUsed\_Count                                                                                   | Live disk space used.                                                                                   |
| Top 5 Size Tables                   | cassandra\_Storage\_Load\_Count                                                                                                     | Top 5 size tables for the Storage used for Cassandra data in bytes                                      |
| Total Disk Usage      | cassandra\_Storage\_Load\_Count                                                                                                     | Total disk usage for the Storage used for Cassandra data in bytes                                       |
| Number Of Active Tasks           | cassandra\_ThreadPools\_ActiveTasks\_Value                                                                                          | Current number of active tasks                                                                          |
| Number Of Completed Tasks          | cassandra\_ThreadPools\_CompletedTasks\_Value                                                                                       | Total number of completed tasks                                                                         |
| Number Of Tasks That Were Blocked  | cassandra\_ThreadPools\_TotalBlockedTasks\_Count                                                                                    | Total number of blocked tasks                                                                           |
| Pending Tasks                | cassandra\_ThreadPools\_PendingTasks\_Value                                                                                         | Total number of pending tasks                                                                           |
| Currently Blocked Tasks         | cassandra\_ThreadPools\_CurrentlyBlockedTasks\_Count                                                                                | Current number of blocked tasks                                                                         |
| Heap Memory Used   | java\_Memory\_HeapMemoryUsage\_used                                                                                                 | Volume of heap memory used                                                                              |
| Non-Heap Memory Used  | java\_Memory\_NonHeapMemoryUsage\_used                                                                                              | Volume of non-heap memory used                                                                          |
| Garbage Collection Time       | java\_GarbageCollector\_ParNew\_CollectionTime, java\_GarbageCollector\_ConcurrentMarkSweep\_CollectionTime                         | Amount of time spent garbage collecting                                                                 |
| Garbage Collections    | java\_GarbageCollector\_ParNew\_CollectionCount, java\_GarbageCollector\_ConcurrentMarkSweep\_CollectionCount                       | Total number of garbage collection events                                                               |
| Exceptions Count                            | cassandra\_ClientRequest\_Timeouts\_Count, cassandra\_ClientRequest\_Unavailables\_Count, cassandra\_ClientRequest\_Failures\_Count | Number of request timeouts, request being unavailable and request failures.                             |
| Unavailable Exceptions Count   | cassandra\_ClientRequest\_Unavailables\_Count                                                                                       | Number of times when a request is unavailable.                                                          |
| Timeout Exceptions Count  | cassandra\_ClientRequest\_Timeouts\_Count                                                                                           | Number of times there is a request timeout.                                                             |
| Transaction Failures Exceptions Count | cassandra\_ClientRequest\_Failures\_Count                                                                                           | Number of times there is a request failure.                                                             |
| Storage Exceptions Count   | cassandra\_Storage\_Exceptions\_Count                                                                                               | Number of unhandled exceptions.                                                                         |
