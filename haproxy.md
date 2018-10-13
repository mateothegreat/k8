---
description: Using HAproxy as an external LoadBalancer in front of your Kubernetes Cluster.
---

# HAproxy

{% code-tabs %}
{% code-tabs-item title="haproxy-network-allowed.cfg" %}
```yaml
frontend www

  bind *:80
  bind *:443 ssl crt /etc/some/cert.pem
  
  #
  # Route based on source ip
  #
  # acl network_allowed src 1.1.1.1 2.2.2.2
  # tcp-request connection reject if !network_allowed
  # acl block_1 src 192.167.0.0/16
  # acl block_2 src 192.168.0.0/16
  #
  # use backend block_1_hosts if block_1 
  # use backend block_2_hosts if block_2
  
  use_backend k8-cluster
  
backend k8-cluster

  server node1 10.10.0.11:12345 check
  server node2 10.10.0.12:12345 check
  server node3 10.10.0.13:12345 check
```
{% endcode-tabs-item %}
{% endcode-tabs %}

