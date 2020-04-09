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

You can pass in each option to the command line to specify tha particular aspect. As an example, if you'd like the dbpath to be different, you can run `mongod --dbpath /data/extra/db`.

Here's a full [list](https://docs.mongodb.com/manual/reference/program/mongod/) of the options when starting mongod. It can take a lot of work to type in every command line option, so often times, we can store these options in a MongoDB config file. See examples and usages of it on their [config documentation](https://docs.mongodb.com/manual/reference/configuration-options/). Note that these don't correspond 1-1 with the command line options, and there are sometimes multiple items that must be specified in the config file to achieve the same command line option. The MongoDB config is stored as in a **YAML** format.

Using the same dbpath example, the config file would look like:

```
storage:
   dbPath: "/data/extra/"
```

After saving it as a `mongod.conf` file, you can run mongod with the config like this: `mongod --config /etc/mongod.conf`.

### Here's a more robust example

Requirements:
- run on port 27000
- data files are stored in /data/db/
- listens to connections from the IP address 192.168.103.100 and localhost
- authentication is enabled

mongod.conf file equivalent:
```
systemLog:
   destination: file
   path: "/var/log/mongodb/mongod.log"
storage:
   dbPath: "/data/db/"
net:
   bindIp: 192.168.103.100, localhost
   port: 27000
security:
    authorization: enabled
```

### File structure (inside /data/db/)

Note, none of the files here are meant for regular users to inspect or modify.
- WiredTiger.lock is a file that prevents other mongod instances from using that directory
- *.wt are storage files for collection or index data
- /diagnostics.data folder contains diagnostics data
- /journal folder contains journal data. Writes are actually buffered 60 seconds in memory
- mongod.lock is similar to WiredTiger.lock and mongo processes cannot access that folder

### Basic commands and shell wrappers/helpers with examples - generally stick with the helper methods
- db.<method>() - database commands
  - User management -> `db.createUser()` and `db.dropUser()`
  - Collection management -> `db.renameCollection()`, `db.collection.createIndex()` and `db.collection.drop()`
  - Database management -> `db.dropDatabase()` and `db.createCollection()`
  - Database status -> `db.serverStatus()`
- rs.<method>() - replica set commands
- sh.<method>() - sharded commands

Note, these methods are for ease of use on our side, each of them actually calls a function like this: `db.runCommand({<command stuff>})`. One more thing to note is that the `db` that we've been referring to always refers to the *active* database (from the `use` command).
Here's an example of the differences between the database command and shell helper:

Shell wrapper/helper:
```
db.<collection>.createIndex(
  { "product": 1 },
  { "name": "name_index" }
)
```

Database command:
```
db.runCommand(
  { "createIndexes": <collection> },
  { "indexes": [
    {
      "key": { "product": 1 }
    },
    { "name": "name_index" }
    ]
  }
)
```

### Logging

**Process log** - this is generally the activity on the mongodb instance (ex. *querying* and *writing* should all show up here)

**MongoDB verbosity levels**
- -1 = inherit from parent
- 0 = default verbosity  (info level)
- 1-5 = increased verbosity like debug

We can look at the process logs through the shell or using some sort of utility (such as `tail`). In the shell, you can run `db.adminCommand({"getLog": "global"})` to get ALL the logs - will give logs from the point we run the command onwards. There's also a very cool tool called [Edda](https://www.mongodb.com/blog/post/edda-a-log-visualizer-for-mongodb) which can seem to visualize the log file nicely. Otherwise, the logs can also be pumped to a 3rd party tool (such as [Loggly](https://www.loggly.com/)) and visualized through their dashboards.

To set the verbosity level of each of the comments through the shell, you can run `db.setLogLevel(0, "<LOG COMPONENT>")`. To se the *index* logs to 0 verbosity level, run `db.setLogLevel(0, "index")`.

**MongoDB log message severity levels (a single letter right after the timestamp)**
- F - Fatal
- E - Error
- W - Warning
- I - Info
- D - Debug

Most of the logs are relatively straight forward, but there a few things that are good to note. The very last parameter that say `<number>ms` is the number of milliseconds the action took - this could be very useful in debugging slow commands. The forth parameter that may look like `[conn3]` is essentially an identifier for the client. This means if this is the same in multiple logs, it was the same client that issue the command that generated the log.

## 2. Replication <a name="replication"></a>

## 3. Sharding <a name="sharding"></a>

