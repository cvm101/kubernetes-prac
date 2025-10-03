Kubernetes Notes

AppConfig

* Used to store configuration data (like URLs, credentials, environment variables) separate from code.
* Docker only replicates containers, but Kubernetes allows defining a blueprint (Deployment/ConfigMap) with specifications.
* StatefulSet: manages stateful applications like databases, ensuring pods have stable IDs and synchronized operations.

Kubernetes Architecture

Node (Worker Node)

* A worker machine where application pods run.
* Pod: the smallest deployable unit in Kubernetes (can contain one or more containers).
* Kubelet: an agent on each node that ensures containers are running inside pods.
* Kube-proxy: handles network rules and enables communication inside and outside the cluster.
* Services: define how pods talk to each other or to external users.

Master Node (Control Plane)

* Manages and controls the cluster, making scheduling and state decisions.
* API Server: entry point for all commands; handles authentication and request validation.
* Scheduler: assigns pods to suitable nodes based on resource requirements and availability.
* Controller Manager: continuously monitors the cluster state and fixes mismatches (e.g., restarts failed pods).
* etcd: distributed key-value database storing the entire cluster state.

Minikube

* A lightweight Kubernetes implementation for local testing and development.
* Runs master and worker processes on a single virtual node using VirtualBox, Docker, or other hypervisors.
* Useful for practice before deploying on real multi-node clusters.

Kubectl

* Command Line Interface (CLI) tool used to interact with Kubernetes clusters.
* Sends commands to the API server.

Common Commands

* kubectl get nodes → lists all cluster nodes
* kubectl get services → lists services
* kubectl create deployment nginx-depl --image=nginx → creates a deployment using nginx image
* kubectl get deployment → shows running deployments
* kubectl get replicaset → shows replicasets created by deployments
* kubectl logs <container-name> → prints logs from a container
* kubectl describe pod <pod-name> → shows detailed information about a pod
* kubectl delete deployment <name> → deletes a deployment
* kubectl apply -f file.yaml → applies a configuration file (-f means file)

Kubectl Object Structure

* Name: unique identifier of the object (pod, service, etc.)
* Specification: desired state (e.g., number of replicas, container image) defined by the user
* Status: actual current state of the object (updated automatically by Kubernetes)
* Metadata: key-value pairs used for identifying and organizing resources (labels, annotations)
* Selectors: match services with the correct pods using labels
* Service: defines networking and connections; targetPort (pod port) must match containerPort (port exposed by container)

