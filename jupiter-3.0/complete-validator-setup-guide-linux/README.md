---
description: >-
  This guide provides all the information for users to set up a node, validator,
  and perform basic health diagnostics on the validator after it is running.
---

# Complete Validator Setup Guide - Linux

### Hardware Recommendations

Currently the recommendation for hardware is to follow the [Cosmos documentation](https://hub.cosmos.network/main/hub-tutorials/join-mainnet.html#hardware).&#x20;

<mark style="color:red;">**Reduce the hardware specifications at your own risk! This may cause validator instability which could lose to the loss of stake and delegated stake positions.**</mark>

### Running As A Background Process

Since the log output of the node will block the terminal and run in the foreground (and will therefore die when the session is ended/closed) it is recommended to use a program to run the node in the background. There are two recommended options:

`screen`

`tmux`

There are also recommendations to run as a background service in the [Cosmos docs](https://hub.cosmos.network/main/hub-tutorials/join-mainnet.html#running-via-background-process).

## PreRequisites

Users must follow the [Mainnet Node Guide](https://app.gitbook.com/o/-L9eUqzwVek3svluhdYd/s/-MlLJH9Bdx\_6-iPFowRp/\~/changes/EsC0KJ4b81pau4c8Sbol/jupiter-3.0/complete-validator-setup-guide-linux/mainnet-node-guide-linux) first.

## Creating a Validator

Creating a validator involves sending a `create-validator` command to the node you wish to validate from. For the purposes of this guide we will be creating a validator on the node which was created based on the [Mainnet Node Guide](https://app.gitbook.com/o/-L9eUqzwVek3svluhdYd/s/-MlLJH9Bdx\_6-iPFowRp/\~/changes/EsC0KJ4b81pau4c8Sbol/jupiter-3.0/mainnet-node-guide-linux).

Creating the validator is as simple as running the following command. Before running this command please read the following:

Running a validator should only be done by experienced Linux System Administrators. When you stake JUP in a validator, that JUP is at risk of being "slashed". Slashing is explained here.

`jupiterd tx staking create-validator --amount=9000000ajup --pubkey=$(jupiterd tendermint show-validator) --moniker="[your node moniker]" --chain-id="jupiter_85-1" --commission-rate="0.01" --commission-max-rate="0.05" --commission-max-change-rate="0.01" --gas="auto" --min-self-delegation="5000000" --from=[keyname] --fees=500ajup`

`--amount // The quantity of staked aJUP`

`--pubkey // The validator's public key`

`--monker // The node moniker which will be doing validation, found in the config.toml file`

`--min-self-delegation // Minimum amount of aJUP required to be delegated from the node operator in order for validation to be performed`

`--from // The name of the key being used to sign the create-validator tx`

### Security

Validator operators must keep security in mind. Validators publicly exposed to the internet may suffer from Distributed Denial of Service (DDoS) attacks which could reduce their uptime and therefore result in slashing of JUP and delegated JUP.&#x20;

Additionally, using the wrong key management techniques could expose your validator's private key to attackers and cause theft of all of your funds.&#x20;

Follow all of the Cosmos [validator security suggestions](https://hub.cosmos.network/main/validators/security.html) and be aware of your validator security at all times.&#x20;

