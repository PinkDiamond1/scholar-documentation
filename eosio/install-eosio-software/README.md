# Install EOS.IO Software

For more detailed instructions, please visit [`Getting Started`](https://github.com/EOSIO/eos/tree/DAWN-2018-03-30-ALPHA#getting-started) from the official EOS.IO Software documentation.

## Clone GitHub Repo

Clone the `eos` repository and run the build script.

> Make sure that you use the `--recursive` parameter

```
$ git clone git@github.com:EOSIO/eos.git --recursive
$ cd eos
```

### Update `git` branch

All EOS Testnet servers must be running on the same `tag` version.

```
$ git checkout tags/DAWN-2018-03-30-ALPHA
```

To confirm you are on the right branch/tag.

```
$ git status
HEAD detached at DAWN-2018-03-30-ALPHA
nothing to commit, working tree clean
```

### Install EOS.IO Software

```
$ ./eosio_build.sh
```

![image](https://user-images.githubusercontent.com/550895/38167725-4c594142-3508-11e8-94a8-0cb04d4dfe55.png)
