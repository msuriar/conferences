# Premise
- How would you design your infrastructure if you couldn't log in? Ever.

# What is a container?
- Application containers
- Unix processes, rather than lightweight VM.
- Applications + dependencies = images
- Runtime environment (cgroups, namespaces, env vars)

# CoreOS
- Container optimised OS
- Minimal operating system (size, features).
- No package managers.
- Automatic updates (atomic).

# Kubernetes
- Container management, scheduling, service discovery.
- API driven application management.
- Agents monitor endpoints for state changes (real-time)
   - Realtime watch based on etcd.
- Controllers enforce desired state.
- Labels identify resources. (nodes, applications, services)

## Resources
- Node
- Pod
- Replication controller
- Service

### Node
- Runs containers, proxies service requests.
- Flannel (networking setup; IP per container)
   - ETCD routing table. Overlay?
- Docker
- Kubelet
   - What things should be running?
- Proxy
- Node is a machine that offers resources to a cluster.

### Pod
- Logical application
- One ore more containers.
- Shared volumes and network namespace
- Identified by ID or labels
- Optionally managed by replication controllers

### Replication Controllers
- Manages replicated set of pods.
- Creates pods from a template.
- Ensures only the specified number of pods are running.
- Rolling updates
- Spefify replicas for each pod by labels.

### Service
- Service discovery primitive for pods.
- Proxy runs on each node.
- IP per service (avoid port collisions)
   - Implication; load balancing requires proxying?
- Basic round-robin algorithm
- Dynamic backends based on label queues.
