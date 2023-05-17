# Comparison of Minikube, Kind, and K3d

## Minikube

Minikube is software that allows users to run a Kubernetes cluster of just a single node and pn a local machine.
It is rather fast to set up and makes for a perfect testing environment for developers to see how their containerized application will run on Kubernetes. 
It is not meant for production, but rather to test applications and deployment settings to see how they fare before sending them to a production environment. Has >25.8k stars on GitHub.

### Pros:
- easy to setup and use;
- GUI availability;
- provides the capability to mount code from the developer’s machine directly into the running Kubernetes node;
- up-to-speed with the official Kubernetes code base thanks to SIG (special interest group) support;
- platform-agnostic;
- kubectl context automatically set to the newly created cluster;
- provides addons that make it easy to install an ingress controller (basic configurations), Helm, Nvidia GPUs, dashboard, etc;
- provides a great deal of flexibility how to run a local single-node cluster;
- very easy and swift to create a new cluster;
- allows creating multiple instances in parallel;
- requires only 2 GB of RAM memory;

### Cons:
- running on Podman is considered experimental;
- highest resource demands;
- poor automation options - no configuration file;
- limited scalability;
- no multi-node support;
- cannot be deployed in the cloud by default;
- unavailable as a managed service;
- not intended for hosting production-grade workloads;
- does not support IoT/edge;
- approach of spawning a VM which decreases the startup speed.

## Kind (Kubernetes in Docker)

Kind is an acronym for “Kubernetes in Docker'' and was born from the idea to run Kubernetes on a container runtime (instead of a virtual machine). Has >11.1k stars on GitHub.

Pros:
- provides solid Podman support;
- CNCF certified;
- platform-agnostic;
- moves the cluster into Docker containers, this leads to a significantly faster startup speed compared to spawning VM (like minicube);
- allows creating multiple instances in parallel;
- provides the possibility to use configuration files;
- ability to load a local images directly into the cluster;

Cons:
- Requires Docker to run Kubernetes clusters, which can impact performance.
- May have a steeper learning curve for certain use cases.

## K3d

k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker.
k3d makes it very easy to create single- and multi-node k3s clusters in docker, e.g. for local development on Kubernetes. Has >4.1k stars on GitHub.

Advantages of K3d:
- Quickly installed and runs on a local machine;
- ingress out of the box;
- platform-agnostic;
- lower resource consumption compared to minikube;
- fully CNCF (Cloud Native Computing Foundation) certified Kubernetes offering;
- provides the capability to mount code from the developer’s machine directly into the running Kubernetes node;
- designed to run production-level Kubernetes on local machines;
- a single binary of less than 50MB;
- kubectl context automatically set to the newly created cluster;
- provides a cluster configuration file in YAML, thus it can be shared across dev team;
- allows quickly deploy production-level Kubernetes in a local environments without much storage or network requirements;
- easily to create single and multi-node k3s clusters for seamless local development and testing;
- more suitable for use in even smaller environments like Raspberry Pi, IoT, and Edge devices;
- provides the ability to create multi-node Kubernetes clusters, allowing testing of more complex scenarios.

Disadvantages of K3d:
- some features supported by official Kubernetes may be limited or not fully supported;
- VM based Kubernetes environment;
- mmore limited when it comes to deploying it on a development machine;
- has a smaller community and ecosystem compared to Minikube or Kind;
- 

## Conclusions

Considering the risks that may arise with Docker licensing and considering the possibility of using an alternative to Podman, only one Kind provides solid Podman support. Thus, I recommend Kind as a further development tool of AsciiArtify.  

## Setup demo


