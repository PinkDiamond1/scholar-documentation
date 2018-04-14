# 测试EOSIO

## Languages

- [Click me switch to English version](README.md)
- [点击查看中文版本](README-ZH.md)
- ~[Haz click para ir a la versión en español](README-ES.md)~
- ~[Cliquez pour passer à la version française](README-FR.md)~

本文我们将会通过以下步骤来跟你解释如何验证EOSIO已经成功安装。

## 目录

- [配置MongoDB](#configure-mongodb)
- [启动MongoDB](#start-mongodb)
- [执行测试脚本](#run-tests)

## 配置MongoDB

**mongod.conf**

你可以使用EOSIO提供的`mongod.conf`配置文件，当然你也可以按照下方的格式来自定义:

> 如果路径不存在，你需要使用`mkdir`手动创建。

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

## 启动MongoDB

运行MongoDB，或者加上`--fork`让它后台运行也可以。

```
$ mongod -f mongod.conf --fork
about to fork child process, waiting until server is ready for connections.
forked process: 26806
child process started successfully, parent exiting
```

使用`tail`命令查看MongoDB最新的log，确保运行期间没有发生错误。

```
$ tail log/mongodb/mongo.log
...
2018-04-06T15:25:10.808+0000 [initandlisten] waiting for connections on port 27017
```

## 执行测试脚本

MongoDB启动以后，你就可以运行EOSIO测试脚本了。

```
$ cd eos/build
$ make test
```

![image](https://user-images.githubusercontent.com/550895/38762716-fe2aee62-3f5c-11e8-8570-986644c6f21a.png)

