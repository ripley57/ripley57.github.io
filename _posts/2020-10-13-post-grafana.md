---
layout: post
title: Grafana
categories:
  - Tools
---
* [Dashboards](https://grafana.com/grafana/dashboards/3387)
* Granfana URL to jump to a specific time range:  
  Haven't tried this yet, but I think it will work: https://grafana.com/docs/grafana/latest/reference/timerange/  
* Annotations:  
  * [Basics](http://chrisbergeron.com/2020/03/08/creating_grafanan_annotations_with_webhooks/)
* [Loki](https://github.com/grafana/loki)
* [promtail](https://github.com/grafana/loki)
* [Grafana vs MS OpsBridge](https://www.g2.com/compare/grafana-vs-micro-focus-operations-bridge-opsbridge)
* [Grafana / Influxdb / Telegraf - capturing windows performance counters](https://thenewstack.io/monitoring-windows-services-with-grafana-influxdb-%E2%80%8Eand-telegraf/)
* [Use Prometheus (and PushGateway) to record process "top" snapshots](https://devconnected.com/monitoring-linux-processes-using-prometheus-and-grafana/)
* [Introduction to Prometheus](https://blog.pvincent.io/2017/12/prometheus-blog-series-part-3-exposing-and-collecting-metrics/)
* [Getting started with Prometheus](https://prometheus.io/docs/introduction/first_steps/)
* [PushGateway](https://prometheus.io/docs/practices/pushing/)
* Querying my Pushgateway manually: `http://nwb-tpccrhes1:9091/metrics`:  
`cpu_usage{instance="nwb-tpccrhes1",job="top",pid="1",process="/usr/lib/systemd/systemd_--system_--deserialize_22"} 0`  
`cpu_usage{instance="nwb-tpccrhes1",job="top",pid="10",process="[rcu_sched]"} 0`  
`cpu_usage{instance="nwb-tpccrhes1",job="top",pid="108",process="[kthrotld]"} 0`  
`cpu_usage{instance="nwb-tpccrhes1",job="top",pid="1083",process="[kdmflush]"} 0`  
* [Prometheus vs InfluxDB](https://www.metricfire.com/blog/prometheus-vs-influxdb/):  
ME: Both are time-series databases. They have different SQL-like query languages; Prometheus's language is briefer than InfluxDB; for example there are functions such as "sum", "avg" and "topk". The main difference is that Prometheus 'scrapes targets' to retrieve the metrics, whereas InfluxDB expects the metrics to be 'pushed' to it, for example using Telegraf. 
* [Windows download](https://grafana.com/grafana/download?platform=windows)
* Influxdb:  
  * [My notes regarding querying the databases created in InfluxDB](https://github.com/ripley57/MF/blob/master/Influxdb.md)
  * [Introduction to Telegraf / InfluxDB](https://docs.influxdata.com/telegraf/v1.14/introduction/)
  * Database(s) location: `C:\Users\testing\.influxdb` 
  * Dropping databases (untested by me): https://community.influxdata.com/t/commad-to-delete-a-particular-series-from-influxdb/5600/7
