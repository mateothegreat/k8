# Docker

### Install Docker One-liner

```bash
curl -sSL https://get.docker.io | bash
```

### Setting up Docker as a Service

```bash
systemctl enable docker
systemctl start docker
usermod -aG docker <your username>
```

### Configure docker to use gcloud

```bash
gcloud auth configure-docker
```



