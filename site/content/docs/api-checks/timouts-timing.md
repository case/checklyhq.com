---
title: Timeouts and timing phases
weight: 5
menu:
  docs:
    parent: "API Checks"
---

All API checks are capped at a timeout of **15 seconds**. With each request, we record the most relevant timing phases. This can help you troubleshoot slow responses, e.g. your DNS might be slow.

The timing phases correspond to to the Node.js request library timing phases:

- `wait`: Duration of socket initialization
- `dns`: Duration of DNS lookup
- `tcp`: Duration of TCP connection
- `firstByte`: Duration of HTTP server response
- `download`: Duration of HTTP download

![](/docs/images/api-checks/timing-phases.png)