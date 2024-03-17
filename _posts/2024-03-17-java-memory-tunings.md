---
title: "Java Memory settings for Containarized Apps"
layout: post
---

# Containarized Applications

Here are some java settings that can be used on containairized applications


```
-XX:+UseG1GC -XX:+PrintGCDetails  -XX:+PrintGCDateStamps -XX:+PrintHeapAtGC  -verbosegc -XX:+UseStringDeduplication  -XX:InitialRAMPercentage=50.0 -XX:MaxRAMPercentage=50.0   
-XX:+PrintFlagsFinal
```

## Other parameters that can be considered

```
-XX:CompressedClassSpaceSize=126m -XX:MaxMetaspaceSize=512m 
```
Note that the values have to be derived based on reviewing the data from APM tools like AppDynamics. 