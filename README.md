# mec-chart

Mobile/Multi-access edge computing (MEC) is one key technology to achieve low-latency performance in cellular networks. It has been determined as a key feature in future 5G networks by both ETSI and 3GPP standardization organizations. It seeks to provide a cloud computing platform at the network edge to be closer to mobile users than conventional cloud systems. Due to emerging low-latency demands, several MEC deployment solutions are being in development. We seek to design an MEC platform that can be easily deployed in 4G LTE networks, as well as may be used as a reference design for future 5G networks.

![](https://i.imgur.com/fYVk1wn.png)

We propose a middlebox approach for the MEC platform deployment in 4G LTE networks. It is standard-compliant and transparent to existing cellular network components, so they need not be modified. The platform sits on the S1 interface, which connects an LTE base station to its core network, and does traffic filtering, manipulation and forwarding. Such middlebox approach has low deployment cost and is easy to install. We have confirmed its viability on both OAI-based and commercial LTE platforms.

This is a demo for MEC system wrapped in **Helm Chart**, and the Docker image is located in Docker Hub ([here](https://hub.docker.com/r/nemsnctu/mec)) for any research experiment. You are able to deploy MEC kernel module to any IoT devices or hosts to reproduce our MEC system kernel features: forwarding module, gtp tunneling module. 

### Built with
- Docker: a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers.
- Helm: a tool for managing Charts which are packages of pre-configured Kubernetes resources.

## Getting Started

### Prerequisites
|          | Version  |
| -------- | -------- | 
|[Docker](https://www.docker.com/) | v19.03.13+ |
|[Helm](https://helm.sh/) | v3.3.4+ |
|[Kubernetes](https://kubernetes.io/)| v1.19.0+ |

You are allowed to install kubernetes in either single node with MicroK8s or Kubeadm to manage your containers and services. 

### Installation

#### Docker
```
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

#### Kubernetes
Here you can use [microk8s](https://microk8s.io/) as orchestrator directly for your attempt to experiment our helm chart.
For convenience, you can use snap to install microk8s.
```
sudo apt update
sudo apt install snapd
sudo snap install microk8s --classic
```

#### Helm
```
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

## Usage
```
helm3 install -f ./mec-chart/values.yaml mec ./mec-chart
```

## Contact
- Maintainer: [f26401004](https://github.com/f26401004) - f26401004@gmail.com
- Project Link: [MEC Middlebox Solution](http://nems.cs.nctu.edu.tw/release/)
