---
layout: post
current: post
cover: assets/images/mongodb/mongodb_cover.jpg
navigation: True
title: MongoDB Cluster Administration Notes [Part 1 - Mongod]
date: 2020-04-12 7:52:00
tags: mongodb, development
class: post-template
subclass: 'post'
author: thomas
---

Mongod - These are summary notes based on [MongoDB Cluster Administration](https://university.mongodb.com/mercury/M103/2020_March_31/overview) course at [MongoDB University](https://university.mongodb.com/).

**Disclaimer**: These are notes I'm taking as I go through the course and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Please rely on the [MongoDB Docs](https://docs.mongodb.com/) first and foremost for any reference material. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com).

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

### Profiling

For slow queries and performance issues, it's not enough to rely solely on the logs. The profiler has information on CRUD, administrative and configuration options.

**Profiler settings**
- 0 - profiler is off and doesn't collect any data. This is the default
- 1 - profiler only collects operation that are slow (> 100 ms)
- 2 - profiles ALL operations; this is a little dangerous as it's a LOT of data

To get and set the profiling levels, use `db.getProfilingLevel()` and `db.setProfilingLevel(level)` respectively. Once the profiler is turned on (using the set command), a `system.profile` collection will appear.

All of this can also be specified in the `mongod.conf` file like this:
```
operationProfiling:
   mode: slowOp
   slowOpThresholdMs: 50
```

### Authentication

**Four types of authentication methods**
- SCRAM - default (salted challenge response authentication mechanism). Basic password security
- X.509 - uses X.509 certificate for authentication (harder to use, but probably more secure)
- LDAP - enterprise authentication
- Kerberos - enterprise authentication

MongoDB also has intra-cluster authentication.

MongoDB uses RBAC (role based access control)
- Each user has one or more roles
  - Each role has one or more privileges
    - Each privilege defines a set of "actions" or a single action that can be performed over a resource

When authentication is enabled, the MongoDB instance will let you authenticate without any credentials on localhost. BUT once you create a user, that will be no longer possible. The standard is to **always** create the administrator user first.

Roles can also have network authentication restrictions such as only being able to connect from a defined IP address or range.

**Built in roles**
- Database User
- Database Administration
- Cluster Administration
- Backup/Restore
- Super User (root)

Roles
- `userAdmin` can only create and drop users, but cannot read/write any data (no data modifications)
- `dbAdmin` can look at stats, indexes, collections, etc. but also cannot read/write any data (no data modifications)
- `dbOwner` can perform any admin function on the database (including read/write). This role technically combines a couple of the other roles to form the dbOwner

**Database tools**
- mongod (already covered - main database process)
- mongo (already covered - shell connection tool)
- mongostat - quick statistics (ops/second, memory, cpu etc.)
- mongodump - exports dump files in bson format
- mongorestore - restores dump files from bson format
- mongoexport - exports data as json (sends output to standard out)
- mongoimport - imports data from json

