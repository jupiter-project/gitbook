---
description: >-
  An initial set of instructions for running a Jupiter Callisto validator. These
  instructions are intended to be followed by competent Linux System admins.
  Lack of knowledge could lead to loss of funds!
---

# Validator Guide - Linux

## Intro

These instructions were written for the Jupiter Testnet (NOT MAINNET) during initial testing of the Cosmos-based Jupiter blockchain. These settings will not work for mainnet and may need to be updated for future testnets. Please report any problems in [Jupiter Discord](https://discord.gg/CdXfUEBDBh)

## Running a Validator

### Add swap

For a more verbose set of instructions use [Digital Ocean's guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-22-04) (the original source of these commands).

> **NOTE: 2 GB may not be adequate, read about calculating the proper swap space**

`df -h`

`sudo fallocate -l 2G /swapfile`

`ls -lh /swapfile`

`sudo chmod 600 /swapfile`

`ls -lh /swapfile`

`sudo mkswap /swapfile`

`sudo swapon /swapfile`

`sudo swapon --show`

`free -h`

`sudo cp /etc/fstab /etc/fstab.bak`

`echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab`

### Install Go

`wget https://go.dev/dl/go1.18.3.linux-amd64.tar.gz`

`sudo su`

`rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.3.linux-amd64.tar.gz`

`export PATH=$PATH:/usr/local/go/bin`

`source ~/.profile`

`go version`

### Install jq

`sudo apt install jq`

### Clone the Jupiter repository

`git clone https://github.com/jupiter-project/jupiter-ng.git`

`cd jupiter-ng`

`git checkout dev`

### Move jupiterd binary:

`sudo mv ./jupiterd /usr/local/bin`

### Run initializer:

`./testnet-init.sh`

Let it run until you see output that blocks are being executed & committed. Then kill it with `CTRL + C`

### Move Genesis:

`cp ./testnet-genesis.json ~/.ethermintd/config/genesis.json`

### Delete Chain Data from Init:

**Warning: This command can be dangerous if not copied correctly!**

`cd ~/.ethermintd/data/`

`rm -rf application.db blockstore.db cs.wal evidence.db snapshots state.db tx_index.db`

`cd ~/jupiter-ng`

### Add a good seed to `seeds=` or `persistent_peers=` in \~/.ethermintd/config/config.toml:

```
# Comma separated list of seed nodes to connect to

seeds = ""

# Comma separated list of nodes to keep persistent connections to

persistent_peers = "ab36dc7a7d916370e16895e10b9249754d4f5708@104.131.166.158:26656"
```

### Fire up the box

`jupiterd start --pruning=nothing --evm.tracer=json --trace --log_level info --minimum-gas-prices=0.0001ajup --json-rpc.api eth,txpool,personal,net,debug,web3,miner --api.enable`
