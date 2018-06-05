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



