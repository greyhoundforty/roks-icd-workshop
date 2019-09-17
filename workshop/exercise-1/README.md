# Exercise 1: Using OpenShift
In this exercise, you'll deploy a simple Node.js Express application. The UI will allow you to write to your hosted IBM Cloud Etcd database as a key/value dictionary app.  You can find the sample application GitHub repository [here](https://github.com/greyhoundforty/s2i-icd).

## Create Project
Access your cluster on the [IBM Cloud clusters dashboard](https://cloud.ibm.com/kubernetes/clusters). Click the `OpenShift web console` button on the top-right. (This is a pop-up so you'll need to white list this site) 

Create a project, you can title it whatever you like, we suggest "roks-icd."

![Create Project](https://dsc.cloud/quickshare/create-project.png)

Click on the name of your project and you will see a view like this:

![Default Project View](https://dsc.cloud/quickshare/initial-project-view.png)

## Add ICD service credentials to cluster
In order for our frontend Node.js app to authenticate with our ICD instance we'll need to take the [Service credentials]() we created previously and add them as an Openshift secret. From the initial prject view click `Resources` in the left hand navigation bar and then select Secrets.

![Adding Secret](https://dsc.cloud/quickshare/add-secret.png)

Click `Create Secret` in the upper right hand of the screen and fill in the following:
 - Secret Type = Generic Secret
 - Secret Name = YOUR_SECRET_NAME
 - Key = `binding`
 - In the provided text box paste in the ICD service credentials that you created earlier. It should begin with `{ "connection": {`

![Adding ICD Connection strings](https://dsc.cloud/quickshare/icd-secret.png)

With the secret added to our project, select `Service Catalog` from the drop down menu in the OpenShift cluster dashboard

![Select Service Catalog](https://dsc.cloud/quickshare/select-service-catalog.png)

## Deploy the sample application 
On the main catalog page scroll down to the Node.js image. Click on that catalog button.

![Find node.js](https://dsc.cloud/quickshare/catalog-listing.png)

Click through to the second step for configuration. Select your project, give your application a name and provide the following git repository `https://github.com/greyhoundforty/s2i-icd`. Choose advanced options. ( a blue hyperlink on the bottom line )

![Click Advanced Options](https://dsc.cloud/quickshare/Shared-Image-2019-09-16-21-19-32.png)

Under the **Context Dir** section put in `/site` and then scroll down until you get to **Deployment Configuration** section. Click the `Add Value from Config Map or Secret` button. 

 - Name = `BINDING`
 - Select a Resource = YOUR_SECRET_NAME
 - Key = `binding`

![Binding ICD secret to application](https://dsc.cloud/quickshare/add-binding-to-app.png)

Scroll to the bottom and click `Create`. Back on the overview page you can watch the image being built and deployed

![Build running](https://dsc.cloud/quickshare/build-running.png)

When the build has deployed, click the 'External Traffic Route', and you should see the login screen like the following

![Dictionary App](https://dsc.cloud/quickshare/front-end-app.png)

Congrats! You've deployed a `Node.js` app to OpenShift using OpenShift Source-to-Image (S2I). You can now add more words to our Etcd backed dictionary app.

## Understanding What Happened

[S2I](https://docs.openshift.com/container-platform/3.6/architecture/core_concepts/builds_and_image_streams.html#source-build) is a framework that creates container images from source code, then runs the assembled images as a containers. It allows developers to build reproducible images easily, letting them spend time on what matters most, developing their code!

## Git Webhooks

(do we want to include this from normal 101 given the time frame - https://github.com/IBM/openshift101/tree/master/workshop/exercise-1#git-webhooks)
