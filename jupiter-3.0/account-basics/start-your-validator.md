# Start your validator

To start your Jupiter v3 validator node

`jupiterd tx staking create-validator --amount=9000000ajup --pubkey=$(jupiterd tendermint show-validator) --moniker="[your node moniker]" --chain-id="jupiter_85-1" --commission-rate="0.01" --commission-max-rate="0.05" --commission-max-change-rate="0.01" --gas="auto" --min-self-delegation="5000000" --from=[keyname] --fees=500ajup`
