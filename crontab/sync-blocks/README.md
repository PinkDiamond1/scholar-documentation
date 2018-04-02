# Scheduled Scripts

Here are some possible scripts which could be executed on a schedule using `crontab -e`.

## Syncing Block

Updating blocks on a long chain could take several hours,
quickly having access to a S3 bucket with the latest blocks will greatly speed up that procedure.

- [`sync-blocks.sh`](sync-blocks.sh)

## Set up Crontab

Using the following configurations, you can quickly set up your cron jobs.

- [`crontab`](crontab)

## AWS CLI

Amazon Web Services offer many great services such as S3 buckets, get started with AWS CLI tools:

https://aws.amazon.com/cli

## Script

**sync-block.sh**
```sh
#!/bin/sh
# EOS Scholar Testnet - Scheduled Scripts
# Sync/Update EOS Blocks to AWS S3 bucket
rm -f /tmp/blocks.tar.gz
tar -zcvf /tmp/blocks.tar.gz /home/ubuntu/data-dir/blocks
/usr/local/bin/aws s3 cp /tmp/blocks.tar.gz s3://scholar.eosnation.io/blocks.tar.gz --acl public-read
```
## Crontab

**crontab**
```sh
AWS_CONFIG_FILE="/home/ubuntu/.aws/config"
*/15 * * * * /home/ubuntu/cron/sync-blocks.sh
```
