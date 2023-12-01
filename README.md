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

eg: Class hash declared: 0x04dcda2c5677b15ab55f0af1ce5ce7b7843e92b703494af7789ae624de843b52

> starkli deploy <CLASS_HASH> <CONSTRUCTOR_INPUTS>

eg: starkli deploy 0x04dcda2c5677b15ab55f0af1ce5ce7b7843e92b703494af7789ae624de843b52 0x285062e7b84487ffa7aca2c1ee4e3fdbfbc7302d8e8806a638fcc050e1b911d

Contract deployed: 0x02040f38c768e5b7cd12e8775d4dbc7387a2f6d2be172adc9c02d509c561f9b7


## call & read contract

> starkli call 0x02040f38c768e5b7cd12e8775d4dbc7387a2f6d2be172adc9c02d509c561f9b7 get_data

> starkli invoke 0x02040f38c768e5b7cd12e8775d4dbc7387a2f6d2be172adc9c02d509c561f9b7 set_data 0x10
Enter keystore password:


# ref

https://book.starknet.io/ch02-01-basic-installation.html

https://github.com/starknet-edu/starknetbook/blob/main/examples/Ownable-Starknet/src/lib.cairo

