# HAproxy

{% code-tabs %}
{% code-tabs-item title="haproxy-network-allowed.cfg" %}
```yaml
frontend www

  mode tcp
  bind *:80  
  
  acl network_allowed src 1.1.1.1 2.2.2.2
  tcp-request connection reject if !network_allowed
  
  acl block_1 src 192.167.0.0/16
  acl block_2 src 192.168.0.0/16

  use backend block_1_hosts if block_1 
  use backend block_2_hosts if block_2
```
{% endcode-tabs-item %}
{% endcode-tabs %}



