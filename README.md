[Link on English Version](https://github.com/b-harvest/cosmos-gaiacli-manual/blob/master/README_en.md)

# 중요 공지사항!!!

해당 내용은 위임자가 키를 복구하거나 위임을 실행하는 과정을 설명합니다.

과정을 실행하는데 있어 발생할 수 있는 모든 위험은 전적으로 실행하는 본인의 책임하에 이뤄져야 합니다!!!



메인넷 제네시스 시각 : UTC 2019-03-13 23:00:00 / Seoul 2019-03-14 08:00:00



# Cosmos Gaiacli Manual

docker 환경을 통한 코스모스 키 복구 및 위임 매뉴얼

Cosmos key recovery and delegation manual by docker image



### docker 설치

[Windows](https://docs.docker.com/toolbox/overview/)

- https://docs.docker.com/toolbox/toolbox_install_windows/

- https://hub.docker.com/editions/community/docker-ce-desktop-windows


[Mac](https://docs.docker.com/docker-for-mac/)

- https://docs.docker.com/docker-for-mac/install/

- https://hub.docker.com/editions/community/docker-ce-desktop-mac





docker의 gaia 최신버젼 확인

- [dockerhub](https://hub.docker.com/r/tendermint/gaia/tags)



### tendermint/gaia의 docker를 pull

```bash
docker pull tendermint/gaia:stable
```



### pull한 gaia docker의 shell 실행

```bash
docker run -it tendermint/gaia:stable /bin/sh
```

- 바이너리파일 경로(binary file path)
```bash
/usr/bin/gaiacli
/usr/bin/gaiad
```


### gaiacli version 확인

```bash
gaiacli version --long
```


### key 복구

```bash
gaiacli keys add [KEYNAME] --recover
```

- [KEYNAME]에 원하는 key 이름을 넣습니다.(사용자가 설정)
  
- 8자이상의 암호를 입력합니다.(이 암호를통해 키가 암호화됩니다)

- 시드단어를 입력합니다.(24단어, ico 참여자는 12단어)


### key 조회

```bash
gaiacli keys list
```

- 키의 이름, 주소, pubkey가 출력됩니다.


### key 삭제

```bash
gaiacli keys delete [KEYNAME]
```

- [KEYNAME]에 삭제하고자 하는 key 이름을 넣습니다.
  

### 잔고확인()

```bash
gaiacli query account [ACCOUNT-ADDR] --chain-id [CHAIN-ID] --node [NODE]
```

- [ACCOUNT-ADDR] : "cosmos"로 시작하는 지갑 주소

- [CHAIN-ID] : 체인ID(메인넷 예:cosmoshub-1)(gaia-13001 테스트넷 예:gaia-13001)

- [NODE] : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657), BHarvest 퍼블릭 노드 주소입니다.


### 위임 transaction 실행

```bash
gaiacli tx staking delegate [VALIDATOR-ADDR] [AMOUNT] --fees [FEES] --from [KEYNAME] --chain-id [CHAIN-ID] --node [NODE]
```

- [VALIDATOR-ADDR] : 위임하고자 하는 검증인의 검증인주소를 입력(cosmosvaloper로 시작되는 주소)
  
- (메인넷/테스트넷 비하베스트 검증인주소 = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- [AMOUNT] : 위임금액을 uatom으로 입력(1atom = 1000000uatom, 메인넷예:1000000uatom, 테스트넷예:1000000muon)
  
- [FEES] : 지출할 fee를 uatom으로 입력(메인넷 예:100000uatom)(gaia-13001 테스트넷 예:200000photino)
 
- [KEYNAME] : 사용할 지갑의 key 이름 입력
  
- [CHAIN-ID] : 체인ID(메인넷 예:cosmoshub-1)(gaia-13001 테스트넷 예:gaia-13001)
  
- [NODE] : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657), BHarvest 퍼블릭 노드 주소입니다.
                                                                
### 위임이동 transaction 실행

```bash
gaiacli tx staking redelegate [FROM-VALIDATOR-ADDR] [TO-VALIDATOR-ADDR] [AMOUNT] --fees [FEES] --from [KEYNAME] --chain-id [CHAIN-ID] --node [NODE]
```

- [FROM-VALIDATOR-ADDR] : 기존 검증인 주소(cosmosvaloper로시작)
  
- [TO-VALIDATOR-ADDR] : 위임하고자 하는 검증인의 검증인주소를 입력(cosmosvaloper로 시작되는 주소)
  
- (메인넷/테스트넷 비하베스트 검증인주소 = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

- [AMOUNT] : 위임금액을 uatom으로 입력(1atom = 1000000uatom, 메인넷예:1000000uatom, 테스트넷예:1000000muon)

- [FEES] : 지출할 fee를 uatom으로 입력(메인넷 예:100000uatom)(gaia-13001 테스트넷 예:200000photino)

- [KEYNAME] : 사용할 지갑의 key 이름 입력

- [CHAIN-ID] : 체인ID(메인넷 예:cosmoshub-1)(gaia-13001 테스트넷 예:gaia-13001)
  
- [NODE] : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657), BHarvest 퍼블릭 노드 주소입니다.

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

