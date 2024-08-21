#### Nodes & Pods
* A pod = the smallest unit of computation, an abstraction over a container. 
* A worker node can have multiple pods. Usually 1 pod per application. A pod can have multiple containers, but this is not usual. 
* Each pod gets its own unique IP address. 
* Pods are *ephemeral* - they're meant to be easily replaceable. This means that communicating with a pod can be tricky because you won't know what the IP address is ahead of time until it's actually running, and the IP address can change. Many workloads can also create multiple pods dynamically, so we won't know how many pods are running for a given application. 
#### Service
A prescriptive config file that handles identifying running pods and their IP addresses. Example service definition:
```
apiVersion: v1
kind: Service
metadata:
  name: api-service
spec:
  selector:
    app: my-api-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```
This creates a *service* named *api-service* in the cluster. This service is bound to any pod running *my-api-app* in the cluster, regardless of how many pods exist or where they are running. As new pods of this type start up, this service definition will automatically discover them. 
#### Ingress

#### Deployment
A controller that tells K8s how to create or modify instances of pods. 
#### ConfigMap
An external configuration to your application. 
#### Secrets
