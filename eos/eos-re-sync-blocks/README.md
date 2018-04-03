# EOS Resync Blocks

As a EOS full-node connecting to an existing EOS network could take quite some time because you need to sync all the existing Blocks.
EOS Scholar Testnet is providing a daily S3 bucket the latest blocks to accelerate that process.

Here are the steps we will cover:

1. Download Blocks
2. Unzip tarbal
3. Restart `eosiod`

### Download Blocks

You will want to download these blocks into your `data-dir` folder.

```bash
$ wget https://s3.amazonaws.com/scholar.eosnation.io/blocks.tar.gz
```

**Downloading via AWS CLI**

If your connection stops or timeout, it would be recommend to use AWS CLI to download the S3 Bucket.

**Install**

```bash
$ pip install awscli
$ aws configure (optional - needed for upload)
```

**Download**
```
$ aws s3 cp s3://scholar.eosnation.io/blocks.tar.gz blocks.tar.gz
(Should see a download progress)
```

## Unzip tarbal

If blocks already exist in the `data-dir`, you should clear both the `blocks` & `shared_mem` folder.

**Delete existing blocks**

```
$ rm -r blocks
$ rm -r shared_mem
$ tar -zxvf blocks.tar.gz
```

## Restart EOS

Once the new blocks are loaded in your `data-dir`, you can restart `eosid` using the `--replay` flag.

```
$ eosiod --replay
```
