---
layout: post
current: post
cover: assets/images/mongodb/mongodb_cover.jpg
navigation: True
title: MongoDB Cluster Administration Notes [Part 2 - Replication]
date: 2020-04-12 7:53:00
tags: mongodb
class: post-template
subclass: 'post'
author: thomas
---

Replication - These are summary notes based on [MongoDB Cluster Administration](https://university.mongodb.com/mercury/M103/2020_March_31/overview) course at [MongoDB University](https://university.mongodb.com/).

**Disclaimer**: These are notes I'm taking as I go through the course and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Please rely on the [MongoDB Docs](https://docs.mongodb.com/) first and foremost for any reference material. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com).

What is replication? This is the concept of maintaining multiple copies of the transactional data. This allows for both better **availability** of existing data and in some cases a read performance boost.

**Binary replication**, the process that replicas are replicated by only reading in exact changes, requires all replicas to be on the same operating system and same database version. This uses less data and is usually faster.

**Statement based replication**, the process where replicas are replicated by reading in op logs, works regardless of operating system or MongoDB version, but a little slower and requires more data. This is what MongoDB uses.

**Idempotency** is the property which an operation when applied multiple times, doesn't change the result of the operation
- Example: x = 5 (idempotent)
- Example: x += 1 (not idempotent)

### MongoDB Replica Sets

This is a number of MongoDB databases (usually an odd number of nodes ex. 3) that have replicated data for high availability and redundancy (along with minor read improvements). There is only one primary node, while the rest are secondary nodes.
- Write are handled by the primary database, and the secondary nodes have that data asynchronously replicated
- Writes on the primary create a statement based op-log in idempotent form (for example, if `$inc` is called, it'll be translated to a lower level `set`)
- A replica set member can also be set as an arbitrator which doesn't hold data, but can vote for a primary when a database instance goes down
  - You may ask, wait, why do I need an arbitrator or why do I need an odd number of MongoDB replica nodes? If I have *two* MongoDB instances, isn't that already redundant?
  - This is a very common misconception because a common set up for REST web applications is to have two instances for redundancy, but the catch there is those service are REST, meaning they don't store state, and thus don't need to communicate with each other. With MongoDB, one of the nodes has to be a primary node and when two nodes can't communicate with each other, neither one knows if the other node is down, so neither can elect itself primary to receive write commands
- The majority of the nodes in the replica set must vote for a primary for the primary fail-over to work
- Having x nodes, where x is an even number, will provide the same availability as having x - 1 nodes. As an example, having four nodes provides the same redundancy as having three nodes - the only minor upside being there's an additional set of data in case of data loss
- There's a max of *seven* voting members in a replica set because more would take too much time to elect a primary for negligible redundancy gain
- Secondary nodes can be set specifically for other purposes such as a **delayed** node - this could be a hot backup for the primary, with a configurable delay in replication
- 