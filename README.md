# Kubernetes Configurations
A bunch of configurations for getting Kubernetes up and running on 3+ Ubuntu Linux servers using K3s from Rancher.
<br>
Documentation for the cluster can be found under the [Cluster](cluster/README.md) directory.

<br>

# My Environment
In my environment, I'm running a total of 5 virtual machines (IP addresses for documentation reference):
 - KubeNode1 (10.175.134.131)
   - Server 1 that runs the Kubernetes API, sits behind the load balancer
   - Configs can be found in [Cluster](/Cluster) 
 - KubeNode2 (10.175.134.132)
   - Server 2 that runs the Kubernetes API, sits behind the load balancer
   - Configs can be found in [Cluster](/Cluster) 
 - KubeAgent1 (10.175.134.141)
   - Agent that will run Kubernetes workloads
   - See [Get Kubernetes token from Node](#get-kubernetes-token-from-node) below
 - KubeDB (10.175.134.133)
   - Database server that stores Kubernetes information
   - Configs can be found in [DB](/DB)
 - KubeProxy (10.175.134.130)
   - NGINX web server acting as a reverse proxy load balancer
   - Configs can be found in [LoadBalancer]([/LoadBalancer)

<br>

## Useful commands

### View current available nodes in k3s Kubernetes Cluster

```bash
sudo k3s kubectl get node
```

<br>

### Get Kubernetes token from Node

```bash
sudo cat /var/lib/rancher/k3s/server/node-token
```

<br>

### Allow user(s) to interface with Docker without sudo

```bash
#Should already exist after installing docker
sudo groupadd docker

sudo usermod -aG docker $USER

#Update docker group data
newgrp docker
```