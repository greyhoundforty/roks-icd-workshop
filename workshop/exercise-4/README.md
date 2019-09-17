# Exercise 4: Autoscale Pods

![Set resource limit on deployment](https://dsc.cloud/quickshare/resource-limitations.png)

![Set Autoscale policy](https://dsc.cloud/quickshare/autoscale.png) 

## Simulate Load on the Application
First, let's simulate some load on our application. Run the following script which will endlessly spam our app with requests:

```bash
while sleep 1; do curl -s <your_app_route>/info ; done
```

Note: Retrieve the external URL from the OpenShift console, or from the URL of your Example Health application. Note that there may be an `/index.html` at the end that you need to replace with `/info`. We're hitting the /info endpoint which will trigger some logs from our app. For example:

## View change in deployment

![Pods scaling up](https://dsc.cloud/quickshare/Shared-Image-2019-09-16-23-39-05.png)

