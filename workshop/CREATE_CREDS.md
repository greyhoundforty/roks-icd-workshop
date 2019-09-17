## Generate Credentials for ICD 
In order for our OpenShift app to talk to our ICD instance, we'll need to generate some service credentials that we can use as container secrets. You will need to wait until the service has been provisioned before you can create service credentials. 

## CLI

```shell 
$ ibmcloud resource service-key-create <name-of-credentials> Administrator --instance-name <Your-Etcd-Service-Name>
```

## Portal
**Go to your ICD instance page, on the left hand navigation click `Service Credentials`**

![](https://dsc.cloud/quickshare/icd-service-creds.png)

**Click on New Credentials, give your credentials a unique name and click `Add`**

![](https://dsc.cloud/quickshare/Shared-Image-2019-09-16-13-41-40.png)