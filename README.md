# kubernetes-and-ansible
This repository has set of ansible playbooks created to setup a kubernetes cluster fully automated with one master and two worker nodes. This will work on physical servers, virtual machines, aws cloud, google cloud or any other cloud servers. This has been tested and verified on Centos 7.3 64 bit operating systems.

How to use this (Setup Instructions)

1. Make your servers ready (one master node and two worker nodes).
2. All nodes must be reachable between master and worker nodes.
3. Internet connection must be enabled in all nodes, required packages will be downloaded from kubernetes official yum repository.
4. Make your host entry in file "hosts" available in "centos" directory.
5. Provide your server details in "env_variables" available in "centos" directory.
6. Deploy the ssh key from master node to other nodes for password less authentication.

   ssh-keygen
   
   Copy the public key to all nodes including your master node and make sure you are able to login into any nodes without password.
   
7. Run "settingup_kubernetes_cluster.yml" playbook to setup all nodes and kubernetes master configuration.

   ansible-playbook settingup_kubernetes_cluster.yml
   
8. Run "join_kubernetes_workers_nodes.yml" playbook to join the worker nodes with kubernetes master node once "settingup_kubernetes_cluster.yml" playbook tasks are completed.

   ansible-playbook join_kubernetes_workers_nodes.yml

9. Verify the configuration from master node.

   kubectl get nodes

Files:
ansible.cfg - Ansible configuration file created locally.
hosts - Ansible Inventory File
env_variables - Main environment variable file where we have to specify based on our environment.
settingup_kubernetes_cluster.yml - Ansible Playbook to perform prerequisites ready, setting up nodes, configure master node.
configure_worker_nodes.yml - Ansible Playbook to join worker nodes with master node.
clear_k8s_setup.yml - Delete entire configurations from all nodes.
playbooks - Its a directory holds all playbooks.

Who we are?
We (learnitguide.net) provide you all complete step by step procedures, How to, Installations, configurations, Implementations, documentations, on-line trainings, easy guides on Linux, Cloud Computing, Openstack, Puppet, Chef, Ansible, Devops, Docker, Kubernetes, Linux clusters, VCS Cluster, Virtualizations and other technologies

For more updates, stay connect with us on
Youtube Channel : https://www.youtube.com/learnitguide
Facebook : http://www.facebook.com/learnitguide
Twitter : http://www.twitter.com/learnitguide
Visit our Website : https://www.learnitguide.net
