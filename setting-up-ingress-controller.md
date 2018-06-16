# Ingress Controller + LetsEncrypt

### Clone the k8-byexamples-ingress-controller repository

```bash
git clone https://github.com/mateothegreat/k8-byexamples-ingress-controller
cd k8-byexamples-ingress-controller
git submodule update --init
```

### Install the ingress controller

Now we can install the ingress controller and it's resources \(RBAC, Deployment, Service\) with the following command:

```bash
make install LOADBALANCER_IP=35.200.108.203
```

### Install cert-manager

```bash
git clone https://github.com/mateothegreat/k8-byexamples-cert-manager
cd k8-byexamples-cert-manager
make install
```

