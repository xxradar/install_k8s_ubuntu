# Automating a K8S install with kubeadm / containerd / calico

## Initialise kubernetes master mode 
```
curl https://raw.githubusercontent.com/xxradar/install_k8s_ubuntu/main/setup.sh | bash
```
Note the kubeadm join command, it looks like ...
```
kubeadm join 10.11.2.231:6443 --token eow8gw.8863eelhollpn37p \
    --discovery-token-ca-cert-hash sha256:1e0ec482fcee39edbf6225e6a7e57217bd1e57c23e2d318ef772fae16759947e
```

## Initialise the kubernetes worker nodes
```
curl https://raw.githubusercontent.com/xxradar/install_k8s_ubuntu/main/setup_node.sh | bash
```
Join every nodes by running the `kubeadm join` command
```
kubeadm join 10.11.2.231:6443 --token eow8gw.8863eelhollpn37p \
    --discovery-token-ca-cert-hash sha256:1e0ec482fcee39edbf6225e6a7e57217bd1e57c23e2d318ef772fae16759947e
```

## Install calico (on master node only)
On the master node, install the calico components
```
curl https://raw.githubusercontent.com/xxradar/install_k8s_ubuntu/main/calico_install.sh | bash
```

## Install a demo application 
```
git clone https://github.com/xxradar/app_routable_demo
cd ./app_routable_demo
./setup.sh
```
