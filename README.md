# 중요 공지사항!!!(Important Notice!!!)

해당 내용은 위임자가 키를 복구하거나 위임을 실행하는 과정을 설명합니다.

This manual explains how to recover key and to delegate.

과정을 실행하는데 있어 발생할 수 있는 모든 위험은 전적으로 실행하는 본인의 책임하에 이뤄져야 합니다!!!

Every risk associated with the procedure is totally upon each executor himself or herself!!!

메인넷 제네시스 시각 : UTC 2019-03-13 23:00:00 / Seoul 2019-03-14 08:00:00

Mainnet Genesis Time : UTC 2019-03-13 23:00:00

# Cosmos Gaiacli Manual

docker 환경을 통한 코스모스 키 복구 및 위임 매뉴얼

Cosmos key recovery and delegation manual by docker image



### docker 설치(install docker)

[Windows](https://docs.docker.com/toolbox/overview/)

- https://docs.docker.com/toolbox/toolbox_install_windows/

- https://hub.docker.com/editions/community/docker-ce-desktop-windows


[Mac](https://docs.docker.com/docker-for-mac/)

- https://docs.docker.com/docker-for-mac/install/

- https://hub.docker.com/editions/community/docker-ce-desktop-mac





docker의 gaia 최신버젼 확인(check latest version of gaia on docker)

- [dockerhub](https://hub.docker.com/r/tendermint/gaia/tags)



### tendermint/gaia의 docker를 pull(pull docker image of tendermint/gaia)

```bash
docker pull tendermint/gaia:stable
```



### pull한 gaia docker의 shell 실행(get shell of docker)

```bash
docker run -it tendermint/gaia:stable /bin/sh
```

- 바이너리파일 경로(binary file path)
```bash
/usr/bin/gaiacli
/usr/bin/gaiad
```


### gaiacli version 확인(check gaiacli version)

```bash
gaiacli version --long
```


### key 복구(key recovery)

```bash
gaiacli keys add [KEYNAME] --recover
```

- [KEYNAME]에 원하는 key 이름을 넣습니다.(사용자가 설정)
  
- put key name in [KEYNAME].(determined by user)
  
  
- 8자이상의 암호를 입력합니다.(이 암호를통해 키가 암호화됩니다)

- input password for this key.(key will be encrypted by this password)


- 시드단어를 입력합니다.(24단어)

- enter mnemonic(24 words)



### key 조회(show key list)

```bash
gaiacli keys list
```

- 키의 이름, 주소, pubkey가 출력됩니다.

- displays name, address, pubkey of each key


### key 삭제(delete key)

```bash
gaiacli keys delete [KEYNAME]
```

- [KEYNAME]에 삭제하고자 하는 key 이름을 넣습니다.
  
- put key name which you want to delete in [KEYNAME]


### 잔고확인(account balance check)

```bash
gaiacli query account [ACCOUNT-ADDR] --chain-id [CHAIN-ID] --node [NODE]
```

- [ACCOUNT-ADDR] : "cosmos"로 시작하는 지갑 주소

- [ACCOUNT-ADDR] : wallet address starting with "cosmos..."


- [CHAIN-ID] : 체인ID(메인넷 예:cosmoshub-1)(gaia-13001 테스트넷 예:gaia-13001)
  
- [CHAIN-ID] : chain ID(mainnet example:cosmoshub-1)(gaia-13001 testnet example:gaia-13001)
  

- [NODE] : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657), BHarvest 퍼블릭 노드 주소입니다.
                                                                
- [NODE] : target node to send transaction to(example:tcp://18.194.218.14:26657) , BHarvest public node


### 위임 transaction 실행(execute delegation transaction)

```bash
gaiacli tx staking delegate [VALIDATOR-ADDR] [AMOUNT] --fees [FEES] --from [KEYNAME] --chain-id [CHAIN-ID] --node [NODE]
```

- [VALIDATOR-ADDR] : 위임하고자 하는 검증인의 검증인주소를 입력(cosmosvaloper로 시작되는 주소)
  
- (메인넷 비하베스트 검증인주소 = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- (* 테스트넷 비하베스트 검증인주소 = cosmosvaloper1cvs6f2nrdwqa9et70vpl5tm56ux4z95ma3dh68)

- [VALIDATOR-ADDR] : put validator address of whom you want to delegate to(validator address starts with "cosmosvaloper...")
  
- (mainnet BHarvest validator address = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- (* testnet BHarvest validator address = cosmosvaloper1cvs6f2nrdwqa9et70vpl5tm56ux4z95ma3dh68)


- [AMOUNT] : 위임금액을 uatom으로 입력(1atom = 1000000uatom, 메인넷예:1000000uatom, 테스트넷예:1000000muon)
  
- [AMOUNT] : put amount of uatom you want to delegate(1atom = 1000000uatom, mainnet example:1000000uatom, testnet:1000000muon)
  

- [FEES] : 지출할 fee를 uatom으로 입력(메인넷 예:100000uatom)(gaia-13001 테스트넷 예:200000photino)
  
- [FEES] : put amount of uatom for fee(mainnet example:100000uatom)(gaia-13001 testnet example:200000photino)
  

- [KEYNAME] : 사용할 지갑의 key 이름 입력
  
- [KEYNAME] : put key name of your wallet
  

- [CHAIN-ID] : 체인ID(메인넷 예:cosmoshub-1)(gaia-13001 테스트넷 예:gaia-13001)
  
- [CHAIN-ID] : chain ID(mainnet example:cosmoshub-1)(gaia-13001 testnet example:gaia-13001)
  

- [NODE] : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657), BHarvest 퍼블릭 노드 주소입니다.
                                                                
- [NODE] : target node to send transaction to(example:tcp://18.194.218.14:26657) , BHarvest public node
                                                                                  

### Q & A

- telegram : https://t.me/joinchat/JzGO-BXmbVtheePYJTGLHQ

- kakaotalk : https://open.kakao.com/o/gIX4tWfb

