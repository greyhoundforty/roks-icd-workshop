# OpenShift 101

Learn the Basics of Red Hat OpenShift on IBM Cloud

Red Hat OpenShift represents a common platform, based on the industry-standard Kubernetes, that allows you to build on premises, on the IBM Cloud, or on any other leading cloud platform. You want freedom of choice; Red Hat OpenShift offers exactly that.

In this lab we'll cover using the OpenShift platform on the IBM Cloud and the common developer loop around cloud native applications including:

 - Kubernetes Basics
 - OpenShift Basics
 - Deploying an IBM Cloud Database 
 - Deploying an application
    - Source-to-Image (s2i)
 - Reading logs and monitoring the application
    - Console Logs
    - Terminal logs 
 - Grafana
 - Scaling the application
    - Resource Limits
    - Horizontal Pod Autoscaler
 - Health Checks
    - Introduce failure
- Readiness and Liveness Probes (maybe?)

* [Workshop](README.md)
    * [Deploy ICD Instance](ICD.md)
    * [Create account and get cluster](GETSTARTED.md)
    * [Setup CLI Access for the cluster](exercise-0/README.md)
    * [Exercise 1: Using OpenShift](exercise-1/README.md)
    * [Exercise 2: Metrics and Dashboards](exercise-2/README.md)
    * [Exercise 3: Autoscale Pods](exercise-3/README.md)
    * [Exercise 4: Liveness and Readiness Probes or health checks](exercise-4/README.md) 