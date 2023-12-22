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
