# Ingress Controller + LetsEncrypt

### Install cert-manager \(optional\)

```bash
git clone https://github.com/mateothegreat/k8-byexamples-cert-manager
cd k8-byexamples-cert-manager
git submodule update --init
make install
```

### Clone the k8-byexamples-ingress-controller repository

```bash
git clone https://github.com/mateothegreat/k8-byexamples-ingress-controller​
cd k8-byexamples-ingress-controller
git submodule update --init
```

### Install the ingress controller

Now we can install the ingress controller and it's resources \(RBAC, Deployment, Service\) with the following command:

```bash
make install LOADBALANCER_IP=35.200.108.203
```

### Create Ingress Resource & Certificate Request

We need an _**Ingress Resource**_ which maps our hostname \(and/or paths\) to a specific service.  
We will also create a "Certificate Request" Resource which will request an **SSL certificate** to be issued from LetsEncrypt.org by means of our cert-manager deployed pod.

```bash
make issue HOST=<yourdomain.com> SERVICE_NAME=<service> SERVICE_PORT=<port>
```

Now you will be able to access your service via the hostname and/or LOADBALANCER\_IP \(above\).

