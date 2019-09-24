# Exercise 3: Metrics and Dashboards

In this exercise, we'll explore the third-party monitoring and metrics dashboards that are installed for free with OpenShift!

## Simulate Load on the Application
First, let's simulate some load on the application so we can gather metrics in Grafana that we'll use in later to set up `Resource Limits`. Jump to your local terminal and run the following script which will endlessly spam our app with requests: 


```bash
while sleep 1; do curl -s <your_app_route>/info > /dev/null 2>&1; done
```

*Note: Retrieve the external URL from the OpenShift console. 

We're hitting the `/info` endpoint which will trigger some logs from our app and help drive up utilization*
With that running in the background we'll take a look at the built in monitoring and logging tools.

## Grafana

Red Hat OpenShift on IBM Cloud comes with [Grafana](https://grafana.com/) preinstalled. Get started by switching to the `Cluster Console` view:

![Cluster Console](https://dsc.cloud/quickshare/console-cluster-view.png)

Then Navigate to `Monitoring > Dashboards` in the left-hand bar. You'll be asked to login with OpenShift and then click through some permissions.

![Monitoring Dashboards](https://dsc.cloud/quickshare/metrics.png)

You should then see your Grafana dashboard. Hit `Home` on the top left, and choose `K8s / Compute Resources / Namespace`.

![Grafana](https://dsc.cloud/quickshare/grafana-namespace.png)

Choose the name of the project you created in Step 1 - the same one that your application is running inside.

You should be able to see the CPU and Memory usage for your application. In production environments, this is helpful for identifying the average amount of CPU or Memory your application uses, especially as it can fluctuate through the day. We'll use this information in the next exercise to set up auto-scaling for our pods.

![Grafana also project](https://dsc.cloud/quickshare/grafana-graph.png)

## Promtheus and Alert Manager

Navigating back to the cluster console, you can also launch:

* **[Prometheus](https://prometheus.io/)** - a monitoring system with an efficient time series database
* **[Alertmanager](https://prometheus.io/docs/alerting/alertmanager/)** - an extension of Prometheus focused on managing alerts

![Metrics, Alerts and Dashboards](https://dsc.cloud/quickshare/metrics.png)

## Prometheus
Monitoring is obviously an important part of managing applications deployed within your OpenShift Cluster. OpenShift includes [Prometheus](https://prometheus.io/docs/introduction/overview/) baked in. Prometheus is a powerful open-source monitoring tool that can pull in metrics from various sources and store them in a time-series database. It offers a powerful query language and the ability to visualize data using third-party tools like the aforementioned Grafana.

![Prometheus](https://dsc.cloud/quickshare/prometheus-graph.png)

## Alertmanager
Alerting with Prometheus is separated into two parts. Alerting rules in Prometheus servers send alerts to the [Alertmanager](https://prometheus.io/docs/alerting/alertmanager). The Alertmanager then manages those alerts, including silencing, inhibition, aggregation and sending out notifications via methods such as email, on-call notification systems, and chat platforms.

![Alert Manager](https://dsc.cloud/quickshare/alertmanager.png)