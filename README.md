# Homelab

Homelab is a project to set up a simple [Kubernetes](https://kubernetes.io/)
(k8s) cluster on a set of microcomputers. The original Homelab project was setup on a
set of Raspberry Pis; 1 Raspberry Pi 3B and 3 Raspberry Pi 4s.

# Building the Cluster

Details of building the cluster can be found at the
[Homelab page](https://www.organic-robot.com/homelab/#building-the-cluster).

# Ansible Installation and Configuration

The ansible scripts in the [ansible](ansible/) directory will install
[microk8s](https://microk8s.io/) and make configurations required to run the cluster.
Note, the files currently assume that the cluster nodes are running an OS that support
the [snap](https://snapcraft.io/) package manager.

Before using Ansible to install and configure the cluster, you should check that all
nodes configured in the `ansible/inventory.yml` are reachable. You can test this with
Ansible's ping module. Run the command:

```
ansible -m ping -i inventory.yml all --user ubuntu
```

To install and configure the cluster cd into the `ansible` directory and run the
command:

```
ansible-playbook -i inventory.yml site.yml
```

Note that these commands assume the remote user (that is, the user on the cluster nodes)
is `ubuntu`.
