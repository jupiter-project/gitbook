---
description: How to create, view, and use your Jupiter account
---

# Account Basics

This is a quick guide to creating your Jupiter v3 wallet and addresses.&#x20;

To create the initial keychain `jupiterd keys add [name]`

To view created recipient address `jupiterd keys list`

To view the node validator address `jupiterd keys [keyname] show --bech=val`

To send JUP `jupiterd tx bank send [sender] [recipient] 1000000000ajup --fees 1000ajup`

To query validator `jupiterd query tendermint-validator-set` (`jupiterd` must be running)

Additional wallet information, to include [backing up and restoring](https://docs.evmos.org/users/wallets/backup.html)
