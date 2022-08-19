---
description: >-
  An initial set of instructions for running a Jupiter Callisto node. At the end
  of this guide you will be running an archive node on the Mainnet and you will
  be supporting the decentralized network!
---

# Mainnet Node Guide - Linux

## Intro

These instructions were written for the Jupiter Mainnet after initial testing of the Cosmos-based Jupiter blockchain. Please report any problems in [Jupiter Discord](https://discord.gg/CdXfUEBDBh).

## Initial Setup

First we want to set up a user to run the node under. It is not recommended to run the node as root, because this comes with various security risks. If the node eventually gets used for validation these risks become much more severe, and could cause lost/stolen funds. Replace the text `username` with the username you wish to use.&#x20;

#### Create the user:

```
useradd username
```

#### **Add the user to the `sudoers` user group so it can elevate privileges as needed:**

```
usermod -aG sudo username
```

#### Switch to the new user:

```
su username
```

## Running a Node

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

It has been noticed that sudo doesn't work directly for installing go, so we want to temporarily switch to the root user for now:

`sudo su`

`rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.3.linux-amd64.tar.gz`

`export PATH=$PATH:/usr/local/go/bin`

`source ~/.profile`

`go version`

Now let's exit to get out of our root user session:

`exit`

### Install jq

`sudo apt install jq`

### Clone the Jupiter repository

`git clone https://github.com/jupiter-project/jupiter-ng.git`

`cd jupiter-ng`

### Copy jupiterd binary:

`sudo cp ./jupiterd /usr/local/bin`

### Run initializer:

`./init.sh`

Let it run until you see output that blocks are being executed & committed. Then kill it with `CTRL + C`

### Replace `init` Genesis:

`cp ./genesis.json ~/.ethermintd/config/genesis.json`

### Delete Chain Data from Init:

<mark style="color:red;">**Warning: This command can be dangerous if not copied correctly!**</mark>

`cd ~/.ethermintd/data/`

<mark style="color:red;">`sudo rm -rf application.db blockstore.db cs.wal evidence.db snapshots state.db tx_index.db`</mark>

`cd ~/jupiter-ng`

### Update Your Node's Moniker

A moniker is just a name used to identify your node. After running the init.sh file the moniker will be set to "jupiter" but it should be changed for easier identification of your node on the network and in other jupiterd commands.&#x20;

Update `moniker="jupiter"` in the config.toml file with the following command:

`nano ~/.ethermintd/config/config.toml`

### Add a good seed to `seeds=` or `persistent_peers=` in \~/.ethermintd/config/config.toml:

```
# Comma separated list of seed nodes to connect to

seeds = ""

# Comma separated list of nodes to keep persistent connections to

persistent_peers = "0ab3cf58979f72af0882ed52a9355b78f5e1eefc@143.198.109.3:26656"
```

### Start The Node

`jupiterd start --pruning=nothing --evm.tracer=json --trace --log_level info --minimum-gas-prices=0.0001ajup --json-rpc.api eth,txpool,personal,net,debug,web3,miner --api.enable`

You should now see your node syncing with the network. Ask in Discord or visit the block explorer (not available yet) to check the current block height so you know how much longer you will be syncing for.&#x20;

### <mark style="color:green;">**Welcome to Jupiter, Astronaut, as we enter the Cosmos!**</mark>
