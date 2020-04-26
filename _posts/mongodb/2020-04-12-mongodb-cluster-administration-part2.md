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
- Writes on the primary create a statement based op log in idempotent form (for example, if `$inc` is called, it'll be translated to a lower level `set`)
- A replica set member can also be set as an arbitrator which doesn't hold data, but can vote for a primary when a database instance goes down
  - You may ask, wait, why do I need an arbitrator or why do I need an odd number of MongoDB replica nodes? If I have *two* MongoDB instances, isn't that already redundant?
  - This is a very common misconception because a common set up for REST web applications is to have two instances for redundancy, but the catch there is those service are REST, meaning they don't store state, and thus don't need to communicate with each other. With MongoDB, one of the nodes has to be a primary node and when two nodes can't communicate with each other, neither one knows if the other node is down, so neither can elect itself primary to receive write commands
- The majority of the nodes in the replica set must vote for a primary for the primary fail-over to work
- Having x nodes, where x is an even number, will provide the same availability as having x - 1 nodes. As an example, having four nodes provides the same redundancy as having three nodes - the only minor upside being there's an additional set of data in case of data loss
- There's a max of *seven* voting members in a replica set because more would take too much time to elect a primary for negligible redundancy gain
- Secondary nodes can be set specifically for other purposes such as a **delayed** node - this could be a hot backup for the primary, with a configurable delay in replication

### Setting up MongoDB Replica Set
- Set up three individual MongoDB instances

Each one would require a security key file to authenticate with each other. In the `mongodb.conf`, make sure a keyFile authentication is specified (for use with other db instances)

```
security:
  authorization: enabled
  keyFile: /var/mongodb/pki/m103-keyfile
```

If you intend for that node to be part of a replica set, you must also specify that in the config like this:

```
replication:
  replSetName: m103-repl
```

You can generate such keyfile using `openssl rand -base64 741 > /var/mongodb/pki/m103-keyfile`.

- Initiate replica set by connecting to one of the nodes using the `mongo` shell.
  
You can call `rs.initiate()` to start the replica set. `rs.status()` lets you see the status of the replica set.

- Add other two nodes to the replica set

This can be done simply be running `rs.add(<replica set connection info>)`. Ensure you have the correct role to perform this operation. Two other quick useful commands: `rs.isMaster()` will tell you if that node is the master (you don't necessarily need to use this command as `rs.status()` works well depending on the use case). If you want to downgrade the current primary from being the primary, use `rs.stepDown()`. This could be useful for upgrading MongoDB versions or other maintenance activity.

Note: if you are running three replicas on a single machine for testing purposes, make sure that the following are different among your instances:
- dbPath
- logPath
- port

### Replication configuration

- `_id` string that identifies the replica set and is needed for the full replica set connection. This is randomly set unless the `replSetName` is set in the `mongod.conf` file:
```
replication:
    replSetName: example-name
```
- `version` number that increments each time the replica set configuration changes (add/remove members, etc.)
- `members` document that includes information on all the replica set submembers

Each of the members have a couple of configuration options, one of the important ones to note is `priority`. This is a number between 0-1000. Numbers with higher priorities will make it more likely to become a primary. If the node is marked as `arbiterOnly` or `hidden`, the `priority` value must be set to 0 (otherwise, an error will occur). The `slaveDelay` option is a number in second that writes from the primary will be synced over -> this also requires the priority to be set to 0 as it doesn't always have the latest transactional data.

### Replication commands
- `rs.status()` gives the general health of the replica
- `rs.isMaster()` tells us whether the node we're connected to is the master node
- `db.serverStatus()` and specifically `db.serverStatus()['repl']` is similar to `rs.isMaster()` but includes the `rbid` the number of rollbacks that have occurred
- `rs.printReplicationInfo()` returns oplog data relative to current node
