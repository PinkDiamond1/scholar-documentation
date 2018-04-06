# Install EOS.IO Software

## Languages

- **[Click me switch to English version](README.md)**
- **[Cliquez pour passer à la version française](README-FR.md)**
- **[点击查看中文版本](README-ZH.md)**
- **[Haz clic en cambiar a la versión en inglés](README-ES.md)**

For more detailed instructions, please visit [`Getting Started`](https://github.com/EOSIO/eos/wiki) from the official EOS.IO Software wiki documentation.

## Clean Install

Clone the `eos` repository and run the build script.

> Make sure that you use the `--recursive` parameter

```
$ git clone git@github.com:EOSIO/eos.git --recursive
$ cd eos
```

### Update from Existing

EOS Scholar Testnets must all be using the same `tag`, therefore if you've previously installed EOS.IO using another release you must update your version to use `dawn-v3.0.0` and update all submodules.

```
$ git pull
$ git checkout tags/dawn-v3.0.0
$ git submodule update --recursive
$ ./eosio_build.sh
```

To confirm you are on the right branch/tag.

```
$ git status
HEAD detached at dawn-v3.0.0
nothing to commit, working tree clean
```

### Install EOS.IO Software

```
$ ./eosio_build.sh
```

![image](https://user-images.githubusercontent.com/550895/38167725-4c594142-3508-11e8-94a8-0cb04d4dfe55.png)
