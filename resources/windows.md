# Windows

## Preparation

### Install Docker

{% code-tabs %}
{% code-tabs-item title="prepare.ps1" %}
```bash
Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
Install-Package -Name Docker -ProviderName DockerMsftProvider
Restart-Computer -Force
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Copy ~/.kube/config from master

Copy the ~/.kube/config from a master node and place it on the windows node under `C:\k\config`

### Download kubectl.exe

{% code-tabs %}
{% code-tabs-item title="get\_kubectl.ps1" %}
```text
Install-Script -Name install-kubectl -Scope CurrentUser -Force
install-kubectl.ps1 -DownloadLocation C:\k
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```bash
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
wget https://github.com/Microsoft/SDN/archive/master.zip -o master.zip
Expand-Archive master.zip -DestinationPath master
mkdir C:/k/
mv master/SDN-master/Kubernetes/windows/* C:/k/
rm -recurse -force master,master.zip
```

### Add to PATH

```text
$env:Path += ";C:\k"
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\k", [EnvironmentVariableTarget]::Machine)

$env:KUBECONFIG="C:\k\config"
[Environment]::SetEnvironmentVariable("KUBECONFIG", "C:\k\config", [EnvironmentVariableTarget]::User)


```

### Creating the "pause" image

Now that `docker` is installed, you need to prepare a "pause" image that's used by Kubernetes to prepare the infrastructure pods.

```bash
docker pull microsoft/windowsservercore:1709
docker tag microsoft/windowsservercore:1709 microsoft/windowsservercore:latest
cd C:/k/
docker build -t kubeletwin/pause .
```

## Other

## Install Chocolatey

```text
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Install kubectl.exe with Chocolatey

```text
choco install kubernetes-cli
```



