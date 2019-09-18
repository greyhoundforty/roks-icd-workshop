# Deploy ICD instances 

In this section, you will login to your own IBM Cloud account, and deploy an IBM Cloud Databases for Etcd instance.

 - Create a new or login with an existing account on https://cloud.ibm.com
 - If you do not have an account, you could create your own [IBM Cloud account](https://cloud.ibm.com/).

Deploy an instance of the [Databases for Etcd](https://cloud.ibm.com/catalog/services/databases-for-etcd) service. For this example you can use the `lite` plan. If you have already provisioned a lite version of Etcd you will need to change `lite` to `standard`.


## CLI 

```shell
$ ibmcloud resource service-instance-create <Your-Etcd-Service-Name> databases-for-etcd lite us-south
```

## Portal
Visit the [Databases for Etcd](https://cloud.ibm.com/catalog/services/databases-for-etcd) service page, select Dallas as the region and the resource group you would like the database deployed in to (`default` most likely)

![Deploy Etcd](https://dsc.cloud/quickshare/deploy-icd.png)


