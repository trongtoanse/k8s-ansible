# K8s Cluster
## Stack
- VirtualBox v7.0
- Ubuntu server v16.04.7 LTS
- K8s v1.21.1
## Diagram
![Diagram](diagram.png)
## Install
### Ping nodes
```
ansible -i inventory/cluster cluster -m ping --user lab --ask-pass
```
### Setup prerequisites
```
ansible-playbook playbooks/prerequisites.yml -i inventory/cluster --user lab --ask-pass --ask-become-pass
```
### Setup kubelet kubeadm kubectl
```
ansible-playbook playbooks/cluster.yml -i inventory/cluster --user lab --ask-pass --ask-become-pass
```
### Setup master nodes
```
ansible-playbook playbooks/master.yml -i inventory/master --user lab --ask-pass --ask-become-pass
```
### Setup worker node
```
ansible-playbook playbooks/worker.yml -i inventory/worker --user lab --ask-pass --ask-become-pass
```
## Cluster
```
NAME            STATUS   ROLES                  AGE   VERSION   INTERNAL-IP     EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
c01-master      Ready    control-plane,master   1d    v1.21.1   192.168.60.20   <none>        Ubuntu 16.04.7 LTS   4.4.0-210-generic   docker://20.10.7
c01-worker-01   Ready    <none>                 1d    v1.21.1   192.168.60.21   <none>        Ubuntu 16.04.7 LTS   4.4.0-210-generic   docker://20.10.7
c01-worker-02   Ready    <none>                 1d    v1.21.1   192.168.60.22   <none>        Ubuntu 16.04.7 LTS   4.4.0-210-generic   docker://20.10.7
c01-worker-03   Ready    <none>                 1d    v1.21.1   192.168.60.23   <none>        Ubuntu 16.04.7 LTS   4.4.0-210-generic   docker://20.10.7
```
