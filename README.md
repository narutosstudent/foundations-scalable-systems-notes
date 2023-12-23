# Notes

Notes of the book Foundations of Scalable Systems.

# Basics

## Introduction to scalable systems

As operational dimensions increase, the system must be able to expand to meet the increased demand. This is known as scalability.

Examples of operational dimensions are:

- The number of simultaneous user or external (e.g., sensor) requests a system can process
- The amount of data a system can effectively process and manage
- The value that can be derived from the data a system stores through predictive analytics
- The ability to maintain a stable, consistent response time as the request load grows

In software systems, we can expand and contract our processing capacity in a matter of seconds to meet instantaneous load.

When we deal with scalability, there are multiple concerns:

- **Performance**: How fast can the system process a request?
- **Availability**: How much of the time is the system available to process requests?
- **Reliability**: How likely is the system to fail while processing a request?
- **Efficiency**: How much of the system's resources are used to process a request?

## Distributed Systems Architectures: An Introduction

### Monolith

We start off with a monolith. They tend to grow quickly in complexity as the application grows. We can scale up. This means upgrading our single server, database etc.

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/85a585b4-f7cf-48c8-8186-5f3248fca1c3)

### Scaling out

Scaling out involves making copies of a service and running them on different servers.

A load balancer receives user requests and selects a server to handle each one, aiming to keep all servers equally busy. It also sends server responses back to the users. Load balancers are a type of reverse proxy, which control user access to servers. They add a small delay to requests and are designed to be very fast to minimize this extra time.

For effective load balancing, the load balancer must be able to send a client's requests to different servers. This requires the servers to be stateless, meaning they don't remember past interactions with a client. For instance, in a shopping cart scenario, the cart's data is stored in a common place, not on the server, so any server can access it when needed for a client's session.

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/14507a50-444e-475e-aaaa-f50b34ca4647)

### Caching

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/8b8a69d8-e5ae-4100-966d-552347184ec1)

Using distributed caching along with scaling up can reduce database queries. This method stores frequently used data in memory for quick access, easing the load on the database. For example, a weather forecast can be cached so many clients can access it without repeatedly querying the database.

### Distributing the database

As more data is added, a distributed database can expand by adding more storage nodes. The data is then evenly distributed across these nodes to balance their storage and processing load.

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/43aa731c-9bc5-4dcc-a3a5-2d6162bb4c7e)

### Multiple processing tiers

The stateless, load-balanced, cached design allows building a multitiered application where a service can request other replicated and balanced services.

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/35f70bb3-0c62-43e7-ad1d-4d736ab40321)

### Increasing responsiveness

Writing a message to a queue is typically much faster than writing to a database, and this enables the request to be successfully acknowledged much more quickly. Another service is deployed to read messages from the queue and write the data to the database.

![image](https://github.com/narutosstudent/foundations-scalable-systems-notes/assets/49603590/0e505b53-3894-4f48-937a-0e24f43560d9)

