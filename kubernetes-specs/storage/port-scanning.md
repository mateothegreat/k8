---
description: >-
  You can use my nmap docker image to perform a network port scan from within
  the cluster by launching the docker-alpine-nmap container below and issuing an
  nmap command pointing to a service within.
---

# Port Scanning

```bash
$ kubectl run --image=appsoa/docker-alpine-nmap --rm -i -t nm -- -Pn -p9200,9300 elasticsearch.es elasticsearch-discovery.es

Starting Nmap 7.40 ( https://nmap.org ) at 2018-02-03 16:54 UTC

Nmap scan report for elasticsearch.es (10.15.248.94)
Host is up (0.0013s latency).

rDNS record for 10.15.248.94: elasticsearch.es.svc.cluster.local

PORT     STATE    SERVICE
9200/tcp open     wap-wsp
9300/tcp filtered vrace

Nmap scan report for elasticsearch-discovery.es (10.15.252.251)
Host is up (0.00018s latency).

rDNS record for 10.15.252.251: elasticsearch-discovery.es.svc.cluster.local

PORT     STATE    SERVICE
9200/tcp filtered wap-wsp
9300/tcp open     vrace

Nmap done: 2 IP addresses (2 hosts up) scanned in 1.41 seconds
```

