---
layout: post
title: Log Forwarding with Syslog-NG
---

Setting the forwarding destination:


```destination d_net { tcp("10.0.11.30" port(1000) log_fifo_size(1000)); };```

Uncomment this:
```log { source(s_src); destination(d_net); };```

To forward a constom log file, create a new file in:

/etc/syslog-ng/conf.d/NAMEOFFILE.conf

For this example we're use fancontrol.conf

```source s_fancontrol {
        file("/home/pi/fan-control.log" follow-freq(1) flags(no-parse));
};```

back in the syslog-ng.conf file, add this:

```log { source(s_fancontrol); destination(d_net); };```

<https://www.syslog-ng.com/technical-documents/doc/syslog-ng-open-source-edition/3.16/administration-guide#TOPIC-956384>
