# What are PODs
A Pod is the basic execution unit of a Kubernetes application--the smallest and simplest unit in the Kubernetes object model that you create or deploy.

Note: you can run single or multiple containers inside one pod.

### three main multi-container pod design patterns

sidecar, ambassador, and adapter.

[Go here to understand in detail](https://kubernetes.io/blog/2015/06/the-distributed-system-toolkit-patterns/)

### Pods are managed by 
Imagine a node/server dies, kubernetes is going to relocate thad pod to another healthy server this is done via following workload resources.

- Deployment
- StatefulSet
- DaemonSet

### Examples 1 - Memory & CPU Limits

[Create a nginx pod with cpu, memory and exposing port 80](yaml_examples/pod-example1.yml)

```
kubectl apply -f yaml_examples/pod-example1.yml
kubectl get pods -n mynamespace

```
### Example 2 - Command and arguments
[Passing command and arguments to the pod](yaml_examples/pod-example2.yml)
```
kubectl apply -f yaml_examples/pod-example2.yml
kubectl get pods
kubectl exec --stdin --tty example-pod-with-nginx-cmd-arg -- cat /proc/1/cmdline
```


### Example 3 - Run as user
[Run pod with security context or run with user or group present on the node](yaml_examples/pod-example3.yml)

```
kubectl apply -f yaml_examples/pod-example3.yml
kubectl get pod example-pod-with-security-context
kubectl logs example-pod-with-security-context
```

### Example 4
[Mount empty volume in pod](yaml_examples/pod-example4.yml)

```
kubectl apply -f yaml_examples/pod-example4.yml
kubectl get pod example-pod-with-security-context
kubectl logs example-pod-with-security-context
```


### Example 5 - MuiltiContainer pod
Notice 2 containers running inside 1 pod.
```
kubectl apply -f yaml_examples/pod-example5.yml
kubectl describe pod example-pod-multicontainer
```


### Example 6 - Using configmap inside pod as file
```
kubectl apply -f yaml_examples/pod-example6-config.yml
kubectl apply -f yaml_examples/pod-example6.yml
kubectl exec  -it example-pod-configmap -- cat /etc/myconfig/game-special-key
```

### Example 7 - Using Liveness probe and readiness probe
```
kubectl apply -f yaml_examples/pod-example7.yml
```
