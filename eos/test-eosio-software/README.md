# Test EOS.IO Software

In this document we will explain to you how to verify if your installation was successful using the following steps:

## Table of Content

- [Configure MongoDB](#configure-mongodb)
- [Start MongoDB](#start-mongodb)
- [Run Tests](#run-tests)

## Configure MongoDB

**mongod.conf**

Use your the `mongod.conf` configuration suggested by EOS.IO software. You can also customize your MongoDB configurations similar to the following:

> If the `path` folder does not exist, you will need to create it using `mkdir`.

```
systemLog:
  destination: file
  path: /home/ubuntu/.eos/log/mongodb/mongo.log
  logAppend: true
storage:
  dbPath: /home/ubuntu/.eos/mongodb
net:
  bindIp: 127.0.0.1
```

## Start MongoDB

Run MongoDB in the forground or as a background process by including `--fork` as an additional parameter.

```
$ mongod -f mongod.conf --fork
about to fork child process, waiting until server is ready for connections.
forked process: 26806
child process started successfully, parent exiting
```

Inspect your latest MongoDB logs using `tail` and make sure there was no errors during the process.

```
$ tail log/mongodb/mongo.log
...
2018-04-06T15:25:10.808+0000 [initandlisten] waiting for connections on port 27017
```

## Run Tests

After MongoDB has been started, you can now start the EOS tests

```
$ cd eos/build
$ make test
```

![image](https://user-images.githubusercontent.com/550895/38762716-fe2aee62-3f5c-11e8-8570-986644c6f21a.png)

