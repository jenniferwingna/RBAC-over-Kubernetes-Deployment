# RBAC-over-Kubernetes-Deployment
## Introduction
This project will mainly cover the implementation of Role-Based Access Control (RBAC) in Kubernetes which includes different types of users and roles, their scopes, and limitations.
## Content Page
1. [What is Kubernetes](#what-is-kubernetes)
2. [Part 1: Setup and pod deployment](#part-1-setup-and-pod-deployment)
3. [Part 2: Users in Kubernetes](#part-2-users-in-kubernetes)
4. [Part 3: Roles and Rolebindings](#part-3-roles-and-rolebindings)
5. [Part 4: Clusterroles and Clusterrolebindings](#part-4-clusterroles-and-clusterrolebindings)
## What is Kubernetes
### Hotel as a Kubernetes Cluster:
   Imagine a hotel as a Kubernetes cluster. The hotel comprises various departments like reception, housekeeping, kitchen, and maintenance, each performing specific tasks to ensure smooth hotel operations. Similarly, in a Kubernetes cluster, various components work together to manage and maintain containerized applications.

### Nodes vs pods vs containers:
- Nodes: Think of a large hotel with multiple floors and rooms. Each floor can be considered a node, and each room is an individual unit of computing resources available on that node. Nodes are like the floors of the hotel, providing computing resources for Kubernetes applications.

- Pods: In Kubernetes, Pods are the smallest deployable units, which can contain one or more containers. Imagine a Pod as a hotel room, and the containers within it are guests. Pods can run on nodes and share the resources of the node, just like guests sharing the resources of a room.

- Containers: Containers are the basic building blocks of a Pod, where the actual application runs. In the hotel analogy, containers are like the facilities and services that guests use in their hotel room, such as the bathroom, bed, and entertainment amenities. Each container runs a specific application or service and is isolated from other containers to ensure no interference.

### Deployment
| Hotel Management  | Kubernetes Deployment  |
|-------------------|-------------------------|
| Reservation System | Manages creation and scaling of Pods |
| Housekeeping      | Handles rolling updates and scaling of Pods |
| Room Upgrades     | Manages rollout of updated versions of applications |
| Fault Tolerance  | Implements strategies for maintaining application availability |


### Expansion and Scalability:
   Just like a hotel can expand by adding more rooms or floors, a Kubernetes cluster can scale by adding more nodes to accommodate additional containers and handle increased workload demands.

### Flexibility and Portability:
   Guests can check in and out of the hotel without affecting other guests' stays. Similarly, containers in Kubernetes can be deployed, scaled, or terminated independently without affecting other applications' performance.
   
## Part 1: Setup and pod deployment
  - Install minikube and docker first. Once installed, start minikube by `minikube start --driver=docker`
  - Create a namespace named `cy5130-rbac`
  - Edit your deployment file. Your `nginx-deployment.yaml` file should look like this:
    ```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: firstname-nginx1
      labels:
        app: nginx
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: nginx
      template:
        metadata:
          labels:
            app: nginx
        spec:
          containers:
          - name: nginx
            image: nginx:1.14.2
            ports:
            - containerPort: 80
    ```
  - Deploy an nginx cluster in it.
    ```
    kubectl apply -f <file_name>.yaml -n <namespace>
    ```
## Part 2: Users in Kubernetes
## Part 3: Roles and Rolebindings
## Part 4: Clusterroles and Clusterrolebindings
