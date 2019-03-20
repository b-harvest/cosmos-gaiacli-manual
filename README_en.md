# Important Notice!!!

This manual explains how to recover key and to delegate.

Every risk associated with the procedure is totally upon each executor himself or herself!!!

Mainnet Genesis Time : UTC 2019-03-13 23:00:00

# Cosmos Gaiacli Manual

Cosmos key recovery and delegation manual by docker image

### install docker

[Windows](https://docs.docker.com/toolbox/overview/)



- https://docs.docker.com/toolbox/toolbox_install_windows/



- https://hub.docker.com/editions/community/docker-ce-desktop-windows




[Mac](https://docs.docker.com/docker-for-mac/)



- https://docs.docker.com/docker-for-mac/install/



- https://hub.docker.com/editions/community/docker-ce-desktop-mac

check latest version of gaia on docker

- [dockerhub](https://hub.docker.com/r/tendermint/gaia/tags)

### pull docker image of tendermint/gaia

```bash

docker pull tendermint/gaia:stable

```

### get shell of docker

```bash

docker run -it tendermint/gaia:stable /bin/sh

```

binary file path
```bash

/usr/bin/gaiacli

/usr/bin/gaiad

```

### check gaiacli version

```
bash
gaiacli version --long

```

### key recovery

```bash

gaiacli keys add [KEYNAME] --recover

```

- put key name in [KEYNAME].(determined by user)

- input password for this key.(key will be encrypted by this password)

- enter mnemonic(24 words, 12 words for ico participants)

### show key list

```bash

gaiacli keys list

```

- displays name, address, pubkey of each key


### delete key

```bash

gaiacli keys delete [KEYNAME]

```

- put key name which you want to delete in [KEYNAME]

### account balance check

```bash

gaiacli query account [ACCOUNT-ADDR] --chain-id [CHAIN-ID] --node [NODE]

```

- [ACCOUNT-ADDR] : wallet address starting with "cosmos..."

- [CHAIN-ID] : chain ID(mainnet example:cosmoshub-1)(gaia-13001 testnet example:gaia-13001)
  
- [NODE] : target node to send transaction to(example:tcp://18.194.218.14:26657) , BHarvest public node


### execute delegation transaction

```bash
gaiacli tx staking delegate [VALIDATOR-ADDR] [AMOUNT] --fees [FEES] --from [KEYNAME] --chain-id [CHAIN-ID] --node [NODE]
```

- [VALIDATOR-ADDR] : put validator address of whom you want to delegate to(validator address starts with "cosmosvaloper...")
  
- (mainnet/testnet BHarvest validator address = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- [AMOUNT] : put amount of uatom you want to delegate(1atom = 1000000uatom, mainnet example:1000000uatom, testnet:1000000muon)
 
- [FEES] : put amount of uatom for fee(mainnet example:100000uatom)(gaia-13001 testnet example:200000photino)
  
- [KEYNAME] : put key name of your wallet
  
- [CHAIN-ID] : chain ID(mainnet example:cosmoshub-1)(gaia-13001 testnet example:gaia-13001)
                                                                
- [NODE] : target node to send transaction to(example:tcp://18.194.218.14:26657) , BHarvest public node


### execute redelegation transaction

```bash
gaiacli tx staking redelegate [FROM-VALIDATOR-ADDR] [TO-VALIDATOR-ADDR] [AMOUNT] --fees [FEES] --from [KEYNAME] --chain-id [CHAIN-ID] --node [NODE]
```

- [FROM-VALIDATOR-ADDR] : validator address in which you currently delegate to(validator address starts with "cosmosvaloper...")
  
- [TO-VALIDATOR-ADDR] : put validator address of whom you want to delegate to(validator address starts with "cosmosvaloper...")
  
- (mainnet/testnet BHarvest validator address = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- [AMOUNT] : put amount of uatom you want to delegate(1atom = 1000000uatom, mainnet example:1000000uatom, testnet:1000000muon)
  
- [FEES] : put amount of uatom for fee(mainnet example:100000uatom)(gaia-13001 testnet example:200000photino)
  
- [KEYNAME] : put key name of your wallet
  
- [CHAIN-ID] : chain ID(mainnet example:cosmoshub-1)(gaia-13001 testnet example:gaia-13001)
                                                                
- [NODE] : target node to send transaction to(example:tcp://18.194.218.14:26657) , BHarvest public node


### Governance

- view proposals

gaiacli query gov proposals --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657

- view proposal status

gaiacli query gov proposal 1 --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657

- view voting status

gaiacli query gov votes 1 --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657

- view deposit status

gaiacli query gov deposits 1 --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657

- vote

gaiacli tx gov vote 1 yes --fees <fees> --from <keyname> --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657

- deposit

gaiacli tx gov deposit 1 50000000uatom --fees <fees> --from <keyname> --chain-id cosmoshub-1 --node tcp://18.194.218.14:26657


### Q & A

- telegram : https://t.me/joinchat/JzGO-BXmbVtheePYJTGLHQ

- kakaotalk : https://open.kakao.com/o/gIX4tWfb
