# Exercise 5: Liveness and Readiness Probes

In Kubernetes, liveness and readiness probes are essential for smoothly running applications. A probe is generally a REST `GET` call, but there are other types of probes available. Liveness probes are used to determine when to restart a container. For example, an application that is unhealthy and no longer responding to an API call would be restarted by OpenShift. Readiness probes determine when a container is ready to start receiving traffic. If a readiness probe fails, then the load balancer would deregister that service.

## Create Readiness and Liveness Probes

Navigate to your deployment and choose `Actions > Edit Health Checks`.

![Health Checks](https://dsc.cloud/quickshare/edit-health.png)

Add a readiness probe:

![Readiness](https://dsc.cloud/quickshare/readiness-probe.png)

We'll put `/healthz` as the path and leave the port as `8080`.

Add a liveness probe:

![Liveness](https://dsc.cloud/quickshare/liveliness-probe.png)

Again, we'll put `/healthz` as the path and leave the port as `8080`. Scroll to the bottom and Click Save.

If all works, everything should be the same. Let's check that the probes are really working though.

## Inject Failure

Let's edit the probe with a typo to see what happens when it fails. Edit the health check and change the path for the readiness probe to `/badpath`. Wait a few minutes and check your deployment - you'll notice that `0/1` containers are ready:

![Badpath](https://dsc.cloud/quickshare/Shared-Image-2019-09-17-16-14-42.png)

Dive into your events and you'll see that the probe is failing, causing the platform to try and repeatedly restart your pod.

![Deeper Dive](https://dsc.cloud/quickshare/monitoring-events.png)

Using health checks gives your OpenShift service layer better reliability and helps you start with a strong foundation.

## You're done

Congratulations on completing the lab!