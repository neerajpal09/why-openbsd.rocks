---
title: "relayd(8)"
---

`relayd` is a daemon to relay and dynamically redirect incoming 
connections to a target host. Its main purposes are to run as a
load-balancer, application layer gateway, or transparent proxy. The
daemon is able to monitor groups of hosts for availability, which
is determined by checking for a specific service common to a host
group. When availability is confirmed, layer 3 and/or layer 7
forwarding services are set up by `relayd`.

```
ext_addr="192.168.1.1"
table <webhosts> { $webhost1 $webhost2 }
relay www {
        listen on $ext_addr port http
        forward to <webhosts> port http loadbalance check http "/" code 200
}
```

Details:

* The `relayd` program, formerly known as `hoststated`, first appeared in OpenBSD 4.1. It was renamed to `relayd` in OpenBSD 4.3. 
* [relayd(8) - OpenBSD manual pages](http://man.openbsd.org/relayd.8)
* [relayd.conf(5) - OpenBSD manual pages](http://man.openbsd.org/relayd.cond.5)
* [relayctl(8) - OpenBSD manual pages](http://man.openbsd.org/relayctl.8)
