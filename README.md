# QUICKSTART

## STEP 1 

```shell
$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
$ cat <<EOF > /etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
$ apt-get update
$ apt-get install -y docker.io kubeadm
```

## STEP 2

```shell
$ git clone https://git quick-k8s
$ cd quick-k8s/kubernetes
$ vim dashboard.yaml
# change <your ip> and <your hostname> Correctly
$ kubeadm init --config kubeadm.yaml
```

## STEP 3

```shell
$ mkdir -p $HOME/.kube
$ sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
$ sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

## STEP 4

```shell
$ kubectl apply -f weave-daemonset.yaml
$ kubectl get pods -n kube-system
```

## STEP 5 

```shell
$ kubeadm join <Your IP>:6443 --token 5n9s47.cmo7gunvt95ingh2 --discovery-token-ca-cert-hash sha256:d3321b231e55706a9283fffcb99e8c9491f1cda0e8a8bc8893f03731c95952db
```

## STEP 6 

Taint/Toleration

```shell
$ kubectl taint node <master node name> foo=bar:NoSchedule
```

or delete Taint/Toleration

```shell
$ kubectl taint nodes --all node-role.kubernetes.io/master-
```

## STEP 7

```shell
$ kubectl apply -f dashboard.yaml
# check admin-user token
$ kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```

- ### [blog](http://http://www.lizhongyuan.net)

- ### 如果对你有帮助，请star和fork