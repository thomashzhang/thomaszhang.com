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

**Disclaimer**: These are notes I’m taking as I go through the course and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I’ve misunderstood. Please rely on the MongoDB Docs first and foremost for any reference material. If you see any mistakes and would like to fix them, please create a PR here.

What is replication? This is the concept of maintaining multiple copies of the transactional data. This allows for both better **availability** of existing data and in some cases a read performance boost.

Binary replication, the process that replicas are replicated by only reading in exact changes, requires all replicas to be on the same operating system and same database version. This uses less data and is usually faster.

Statement based replication, the process where replicas are replicated by reading in op logs, works regardless of operating system or MongoDB version, but a little slower and requires more data. This is what MongoDB uses.

**Idempotency** is the property which an operation when applied multiple times, doesn't change the result of the operation
- Example: x = 5 (good)
- Example: x += 1 (not idempotent)
