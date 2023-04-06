## Kubernetes
- Open-source platform for managing containerized workloads and services.
- Makes it easy to orchestrate many containers on many hosts, scale them as microservices, and deploy rollouts and rollbacks.
- Is a set of APIs to deploy containers on a set of nodes called a cluster.
- Divided into a set of primary components that run as the control plane and a set of nodes that run containers.
- You can descrbe a set of apps and how they should interact with each other and K8s figures how to make that happen.

Pod - A small unit in k8s. Contains unique IP.
Many pods in one cluster.

## GKE
Multiple machines
- Deploy and manage apps.
- Perform admin tasks.
- Set policies.
- Monitor workload health.

Advanced cluster management features include:
- Google Cloud's lb for Compute Engine instances.
- Node pools to designate subsets of nodes within a cluster.
- Automatic scaling of your cluster's node instance count.
- Automatic upgrade for your cluster's node software.
- Node auto-repair to maintain node health and availability.
- Logging and monitoring with Google Cloud's operations suite.

To start up a container cluster with GKE run this command:

    gcloud container cluster create k1
    
## Hybrid and multi-cloud
Distributed systems
- Spreading the computing workload over two or more networked servers.
- Containers break these workloads down into microservices.

### Modern hybrid or multi-cloud architechture
- Move only some of your compute workload to the cloud if you wish.
- Migrate these workloads at your own pace.
- Quickly take advantage of the cloud's flexibility, scalability, and lower computing costs.
- Add specialized services to your compute resources such as machine learning, content caching, data analysis, long-term storage, and IoT toolkit.

## Anthos
- Is a hybrid and multi-cloud solution.
- Framework rests on K8s and GKE On-Prem.
- Provides a rich set of tools for monitoring and maintenance.

### Hybrid architechture
![alt text](https://github.com/lura00/GCP_how-to/blob/main/anthos-hybrid-architechture.PNG)


