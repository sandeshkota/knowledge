### What is Kubernetes
A container orchestration tool (also called as K8s - which 8 chars in b/w K & S)
```
> kubectl apply deploy.yaml
```

### Key Concepts
- Cluster
  - Will have many nodes
- Node
  - will contain many pods
- Pod
  - contains several containers (services from container images)
  - usually 1 conatiner (service) in 1 pod. can have many. ex: 1 service and 1 side car (service mesh) in a pod
- Container
  - Container is an isolated environment within which a service runs 
- Container Image
  - an image through which a service runs in a container. Each application (service, front end, back end, db) is packaged as a container image

### Kubernetes concepts 
- kubectl - K8S control tool
- A node contains: container runtime (docker, ...), kubelet (makes sure containers are running in pod), kube proxy (kube-proxy maintains network rules on nodes)
- service: load balancer that can bring traffic down to collection of pods
- ingress
- configMap
- secrets
- Master node: a node which manages other nodes, monitor, creates/restarts pod if needed, etc.. Contains,
  - API server (front end for K8 control pane)
  - scheduler: control plane component that runs controller processes.
  - control manager: Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.
  - etcd: consistent and highly-available key value store used as Kubernetes' backing store for all cluster data

### Deployment (uses repliac set)
- consider 3 pods are running under a load balancer which is running a service (version v1)
- need to deploy a second version v2, K8 brings up a new pod and checks for liveness (if the pod is running) and then chceks for readiness (if it is working as expected)
- once it is ready, it will add the new pod to the load balancer and remove the other one from the load balancer
- the old pod is destroyed. not a hard destroy. there is a termination grace period - which is the time during which it doesn't take new requests and then it ends




