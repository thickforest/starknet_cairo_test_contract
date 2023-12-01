# step

## install

starkli:

> curl https://get.starkli.sh | sh
> starkliup
> starkli --version

scarb:

> curl --proto '=https' --tlsv1.2 -sSf https://docs.swmansion.com/scarb/install.sh | sh
> scarb --version

## wallet setup

> mkdir -p ~/.starkli-wallets/deployer

> starkli signer keystore from-key ~/.starkli-wallets/deployer/my_keystore_1.json

Enter private key:
Enter password:

> starkli account fetch <SMART_WALLET_ADDRESS> --output ~/.starkli-wallets/deployer/my_account_1.json


## build & deploy contract

> export STARKNET_RPC="https://starknet-mainnet.g.alchemy.com/v2/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
> export STARKNET_ACCOUNT=~/.starkli-wallets/deployer/my_account_1.json
> export STARKNET_KEYSTORE=~/.starkli-wallets/deployer/my_keystore_1.json

> scarb build

> starkli declare target/dev/starknet_cairo_test_contract_ownable.contract_class.json

Class hash declared: <CLASS_HASH>

> starkli deploy <CLASS_HASH> <CONSTRUCTOR_INPUTS>


# ref
https://book.starknet.io/ch02-01-basic-installation.html
https://github.com/starknet-edu/starknetbook/blob/main/examples/Ownable-Starknet/src/lib.cairo

