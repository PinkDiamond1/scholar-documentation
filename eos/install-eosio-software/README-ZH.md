# 安装EOSIO

## Languages

- [Click me switch to English version](README.md)
- [点击查看中文版本](README-ZH.md)~
- ~[Haz click para ir a la versión en español](README-ES.md)~
- ~[Cliquez pour passer à la version française](README-FR.md)~

更多详细，请参考官方wiki文档[`EOSIO入门`].(https://github.com/EOSIO/eos/wiki)

## 全新安装

通过Git clone EOSIO仓库代码并执行安装脚本

> 确保你有的clone命令有带上`--recursive`参数

```
$ git clone https://github.com/EOSIO/eos.git --recursive
$ cd eos
$ git checkout tags/dawn-v3.0.0
$ ./eosio_build.sh
```

## 升级安装

EOS Scholar测试网络一定要确保使用的相同的tag, 所以如果你之前已经安装了EOSIO的另一个版本，那么你必须升级到dawn-v3.0.0，并且升级所有子模块.

```
$ git pull
$ git checkout tags/dawn-v3.0.0
$ git submodule update --recursive
$ ./eosio_build.sh
```

确认你当前使用的是正确的分支

```
$ git status
HEAD detached at dawn-v3.0.0
nothing to commit, working tree clean
```

![image](https://user-images.githubusercontent.com/550895/38167725-4c594142-3508-11e8-94a8-0cb04d4dfe55.png)

## 创建快捷链接

绑定快捷命令，方便后续使用。 

```
$ sudo ln -s /home/ubuntu/eos/build/programs/nodeos/nodeos /usr/local/bin/nodeos
$ sudo ln -s /home/ubuntu/eos/build/programs/cleos/cleos /usr/local/bin/cleos
```

确认快捷命令跟EOS已经正常绑定。

```
$ nodeos --version
3652030188
$ cleos --help
Command Line Interface to EOSIO Client
Usage: cleos [OPTIONS] SUBCOMMAND
```

## 常见问题

Unable to find the requested Boost libraries. 

手动安装Boost 1.66

```
cd ~/opt
wget -c 'https://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.bz2/download' -O boost_1.66.0.tar.bz2
tar xjf boost_1.66.0.tar.bz2
cd boost_1_66_0/
echo "export BOOST_ROOT=$HOME/opt/boost_1_66_0" >> ~/.bash_profile
source ~/.bash_profile
./bootstrap.sh "--prefix=$BOOST_ROOT"
./b2 install
source ~/.bash_profile
```


