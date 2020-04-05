---
layout: post
current: post
cover: assets/images/mongodb/mongodb_cover.jpg
navigation: True
title: MongoDB Cluster Administration Notes
date: 2020-04-05 9:52:00
tags: mongodb
class: post-template
subclass: 'post'
author: thomas
---

These are summary notes based on [MongoDB Cluster Administration](https://university.mongodb.com/mercury/M103/2020_March_31/overview) course at [MongoDB University](https://university.mongodb.com/).

**Disclaimer**: These are notes I'm taking as I go through the course and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Please rely on the [MongoDB Docs](https://docs.mongodb.com/) first and foremost for any reference material. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com).

## Table of contents
1. [**The Mongod**](#mongod) - what's a daemon anyways
2. [**Replication**](#replication) - don't lose the data
3. [**Sharding**](#sharding) - let's get more speed in here

## 1. The Mongod <a name="mongod"></a>

Mongod is the main daemon process that runs continuously to receive commands to interact with the MongoDB database.

### Default Configuration (when running `mongod` without configuration)
- port:27017
- dbpath: /data/db
- bind_ip: localhost
- auth: disabled

## 2. Replication <a name="replication"></a>

## 3. Sharding <a name="sharding"></a>

