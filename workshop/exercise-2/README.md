# Exercise 2: Logging and Monitoring

In this exercise, we'll explore the out-of-the-box logging and monitoring capabilities that are offered in OpenShift.

## OpenShift Logging

Since we only created one pod, seeing our logs will be straight forward. Navigate to `Applications > Pods` menu on the left on the console. You'll see two pods here, one for the build \(marked as Completed\), and one for the pod that is running your application.

![Pods](https://dsc.cloud/quickshare/pods.png)

Click into the `Running` pod and navigate to the `Logs` tab. You should see the Node.js application start-up logs, as well as periodic logs from your curl loop.

![Logs](https://dsc.cloud/quickshare/pod-logs.png)

## OpenShift Terminal

One of the great things about Kuberentes is the ability to quickly debug your application pods with SSH terminals. This is great for development, but generally is not recommended in production environments. OpenShift makes it even easier by allowing you to launch a terminal directly in the dashboard.

Switch to the `Terminal` tab, and run the following commands.

```bash
# This command shows you the the project files.
$ ls
# This command shows you the running processes.
$ ps aux
```

![Terminal](https://dsc.cloud/quickshare/pod-terminal.png)

## OpenShift Monitoring

When deploying new apps, making configuration changes, or simply inspecting the state of your cluster, the OpenShift monitoring dashboard gives you an overview of your running assets. Access the Dashboard now by going to the `Monitoring` tab on the left side menu.

You can also dive in a bit deeper - the `Events` view is very useful for identifying the timeline of events and finding potential error messages. Hit the 'View Details' button on the top right.

![View Details](https://dsc.cloud/quickshare/deploy-events.png)

You'll want to refer to this view throughout the lab. Almost all actions we take in in OpenShift will result in an event being fired in this view. As it is updated real-time, it's a great way to track changes to state.