---
title: "Java Memory settings for Containarized Apps"
layout: post
comments: true
---


# Motivation 

Recent years have seen tremendous growth in enterprise Java applications being modularized into  microservices. 
These services are often deployed as containarized application on Kubernetes (k8s), on premise or on K8s installations on cloud providers like EKS (AWS), AKS (Azure), GKE (Google cloud) etc.
 

## Assumptions 

* A container is primarily dedicated to the Java application 
* Below settings are primarily specified keeping on-premise k8s installations in mind, with focus on low latency 
* Absolute memory values (for container) are specified in k8s manifest file. JVM heap will be specified as % of container memory 

## Java options 
Here are some java settings that can be used for Java version 1.8 and above.


```
-XX:+UseG1GC XX:+DisableExplicitGC 
-XX:+PrintGCDetails  -XX:+PrintGCDateStamps -XX:+PrintHeapAtGC  -verbosegc 
-XX:+UseStringDeduplication -XX:InitialRAMPercentage=50.0 -XX:MaxRAMPercentage=50.0 -XX:NativeMemoryTracking=sumary 
-XX:+PrintFlagsFinal
```

## Other parameters that can be considered

```
-XX:CompressedClassSpaceSize=126m -XX:MaxMetaspaceSize=512m 
```
Note that the values have to be derived based on reviewing the data from APM tools like AppDynamics. 