---
group: cloud-guide
title: Scaling architecture
functional_areas:
  - Cloud
---

The Cloud infrastructure scales according to your resource needs to achieve greater efficiency. The {{site.data.var.ece}} auto-scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance. Converting to this architecture helps to mitigate problems, such as latency, large spikes in traffic, or running out of storage.

## Split architecture

Historically, the Pro architecture consisted of 3 nodes, each containing a full tech stack. The scalable infrastructure provides a tiered solution with a minimum of 6 nodes: 3 nodes for the web server and 3 nodes for the database and other services. This split architecture provides the capability to scale tiers independently to achieve an optimal balance of performance. The database tier scales vertically (increases in size), and the web tier scales horizontally (increases instance count) and vertically (changes instance type and size).

### Database tier scaling

When the database tier approaches capacity, the only way to scale is to increase the server size, such as boosting the CPU power and memory. Capacity is limited to the size of the node that is available.

Further optimizing the database performance includes [scaling the web tier](#web-tier-scaling) and routing traffic. You can route traffic based on the node type. For example, you can serve PHP traffic on the database node or you can isolate the database node from the PHP traffic.

Consider the following when scaling the database tier:

-  Only vertical scaling is available because of the limitations with the technologies used.
-  Non-master database nodes can not be used reliably. (WHY?)

### Web tier scaling

In addition to increasing power and memory, the web tier can scale horizontally by adding extra web servers to an existing cluster when constricted at the PHP level. This complements the vertical scaling provided by the database tier.

Consider the following when scaling the web tier:

-  You must use the same instance type and size for each node. Examples include:
    -  all `M4 xlarge` for WEB
    -  all `C4 xlarge` for DB
-  Instances of a specific type and size must be available when scaling.
-  Must balance the usage of instance types & sizes. (how to describe this??)

## Managing nodes

Pure speculation beyond this point...

-  migrating between instance types
-  routing traffic (load balancing?)
-  monitoring
-  scaling
    - up-sizing
    - down-sizing

### Load balancing