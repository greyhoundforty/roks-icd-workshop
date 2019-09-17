# Deploy ICD instances
Deploy an instance of the [Databases for Etcd](https://cloud.ibm.com/catalog/services/databases-for-etcd) service. For this example you can use the `lite` plan. If you have already provisioned a lite version of Etcd you will need to change `lite` to `standard`.

```
$ ibmcloud resource service-instance-create <Your-Etcd-Service-Name> databases-for-etcd lite us-south
```

## Generate Credentials for ICD via the Portal
In order for our OpenShift app to talk to our ICD instance, we'll need to generate some service credentials that we can use as container secrets. 

**Go to your ICD instance page, on the left hand navigation click `Service Credentials`**

![](https://dsc.cloud/quickshare/icd-service-creds.png)

**Click on New Credentials, give your credentials a unique name and click `Add`**

![](https://dsc.cloud/quickshare/Shared-Image-2019-09-16-13-41-40.png)
