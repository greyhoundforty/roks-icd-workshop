# Exercise 4: Autoscale Pods

In order to see autoscaling in action we'll do the following:

 - Configure resource limitations for our application 
 - Configure an autoscaling policy to meet demand

![Select Application Console](https://dsc.cloud/quickshare/application-project-selection.png)

## Enable Resource Limits
Before we can setup autoscaling for our pods, we first need to set resource limits on the pods running in our cluster. Limits allows you to choose the minimum and maximum CPU and memory usage for a pod.

Navigate to `Applications > Deployments`, then choose your deployment. Then, choose `Actions > Edit Resource Limits`.

![Edit Resource Limits](https://dsc.cloud/quickshare/edit-resource-limit.png)

Hopefully you have your running script simulating load, Grafana showed you that your application was consuming anywhere between ".001" to ".01" cores. This translates to 1-10 "millicores". That seems like a good range for our CPU request, but to be safe, let's bump the higher-end up to 20 millicores. In addition, Grafana showed that the app consumes about 30-45 MB of RAM. Set the following resource limits for your deployment now.

![Set resource limit on deployment](https://dsc.cloud/quickshare/resource-limitations.png)

With the changes made, click Save at the bottom of the screen. Back on the Deployments page you should now see that our pods are redeploying:

![Deploy change](https://dsc.cloud/quickshare/resource-change-deploy.png)
 
## Enable Autoscaling
Now that we have resource limits, let's enable autoscaler. Go back to the deployment, but this time choose `Actions > Edit Autoscaler`.

By default, the autoscaler allows you to scale based on CPU or Memory. The UI allows you to do CPU only (for now). Pods are balanced between the minimum and maximum number of pods that you specify. With the autoscaler, pods are automatically created or deleted to ensure that the average CPU usage of the pods is below the CPU request target as defined. In general, you probably want to start scaling up when you get near 50-90% of the CPU usage of a pod. In our case, let's make it 1-2% to test the autoscaler since we are generating minimal load.

![Set Autoscale policy](https://dsc.cloud/quickshare/autoscale.png) 

We'll set the policy low so we can get a quick rollout of new pods. Set the `CPU Request Target` to 1 or 2. Scroll to the bottom and click `Save`. 

## View change in deployment
On the Deployments page you should now see your deployed pods scaling up from 1 to meet the load from our simulated traffic.

![Pods scaling up](https://dsc.cloud/quickshare/Shared-Image-2019-09-16-23-39-05.png)

That's it! You now have a highly available and automatically scaled front-end Node.js application. OpenShift is automatically scaling your application pods since the CPU usage of the pods greatly exceeded 1% of the resource limit, 30 millicores.