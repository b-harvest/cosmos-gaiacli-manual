# Cosmos Gaiacli Manual

docker 환경을 통한 코스모스 키 복구 및 위임 테스트 매뉴얼

Cosmos key recovery and delegation test manual by docker image



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



### key 복구(key recovery)

```bash
gaiacli keys add <KEYNAME> --recover
```

<KEYNAME>에 원하는 key 이름을 넣습니다.(사용자가 설정)
  
put key name in <KEYNAME>.(determined by user)
  
  
8자이상의 암호를 입력합니다.(이 암호를통해 키가 암호화됩니다)

input password for this key.(key will be encrypted by this password)


시드단어를 입력합니다.(24단어)

enter mnemonic(24 words)



### key 조회(show key list)

```bash
gaiacli keys list
```

키의 이름, 주소, pubkey가 출력됩니다.

displays name, address, pubkey of each key


### key 삭제(delete key)

```bash
gaiacli keys delete <KEYNAME>
```

<KEYNAME>에 삭제하고자 하는 key 이름을 넣습니다.
  
put key name which you want to delete in <KEYNAME>



### 위임 transaction 실행(execute delegation transaction)

```bash
gaiacli tx staking delegate <VALIDATOR-ADDR> <AMOUNT> --fees <FEES> --from <KEYNAME> --chain-id <CHAIN-ID> --node <NODE>
```

<VALIDATOR-ADDR> : 위임하고자 하는 검증인의 검증인주소를 입력(cosmosvaloper로 시작되는 주소)
  
(비하베스트 검증인주소 = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)

<VALIDATOR-ADDR> : put validator address of whom you want to delegate to(validator address starts with "cosmosvaloper...")
  
(BHarvest validator address = cosmosvaloper10e4vsut6suau8tk9m6dnrm0slgd6npe3jx5xpv)


<AMOUNT> : 위임금액을 uatom으로 입력(1atom = 1000000uatom, 예:1000000uatom)
  
<AMOUNT> : put amount of uatom you want to delegate(1atom = 1000000uatom, example:1000000uatom)
  

<FEES> : 지출할 fee를 uatom으로 입력(예:100000uatom)
  
<FEES> : put amount of uatom for fee(example:100000uatom)
  

<KEYNAME> : 사용할 지갑의 key 이름 입력
  
<KEYNAME> : put key name of your wallet
  

<CHAIN-ID> : 체인ID(예:gaia-13001)
  
<CHAIN-ID> : chain ID(example:gaia-13001)
  

<NODE> : transaction을 전송할 대상 노드(예:tcp://18.194.218.14:26657) <- BHarvest 퍼블릭 노드 주소입니다.
                                                                
<NODE> : target node to send transaction to(example:tcp://18.194.218.14:26657) <- BHarvest public node
                                                                                  

### Q & A

telegram : https://t.me/joinchat/JzGO-BXmbVtheePYJTGLHQ

kakaotalk : https://open.kakao.com/o/gIX4tWfb

