---
layout: post
title: geth 설치 및 기본 활용하기
category: 06_BlockChain
tag: [geth, Ethereum]
---



![example](/assets/images/geth.png)

>  geth는 go ethererum의 약자라고 한다. 현재 이더리움 엔진은 C++이나 Python 등 여러 언어로 개발되어 있는데, 그중 go언어로 개발된 geth가 가장 널리 사용되고 있다고 한다. 

---


### 1. geth 설치


먼저 geth를 설치해보자. 설치는 다음 링크를 통해 할 수 있다. 자신의 운영체제에 맞는 것으로 다운받자.

> geth 설치하기: https://geth.ethereum.org/downloads/



### 2. 메인넷 네트워크 연결
- 우선 CLI 명령어를 입력하기 위해 `Windows PowerShell` 로 이동합니다.

- ``` geth --datadir "users/packt/ethereum" --networkid 1 ```
    - `--datadir` 은 블록제인을 저장할 경로를 지정하는데 사용됩니다.


### 3. 개인 네트워크 생성 - 계정 생성

- ` geth account new  `

    - `# geth --datadir . account new ` 는 특정 경로를 지정하는데 사용됩니다.

``` 

PS D:\3_blockChainStudy> geth account new
INFO [10-10|16:33:56.382] Maximum peer count                       ETH=50 LES=0 total=50
Your new account is locked with a password. Please give a password. Do not forget this password.
Password: sj2853
Repeat password: sj2853

Your new key was generated

Public address of the key:   0xe51d1aD2Afd68a71a04b6Ecd8EfB0c522F032FB9
Path of the secret key file: C:\Users\dcjam\AppData\Local\Ethereum\keystore\UTC--2021-10-10T07-34-03.667044900Z--e51d1ad2afd68a71a04b6ecd8efb0c522f032fb9

```
 
 
### 4. 계정의 모든 목록 출력

```
PS D:\3_blockChainStudy> geth account list
INFO [10-10|16:44:28.979] Maximum peer count                       ETH=50 LES=0 total=50
INFO [10-10|16:44:28.991] Set global gas cap                       cap=50,000,000
Account #0: {e51d1ad2afd68a71a04b6ecd8efb0c522f032fb9} keystore://C:\Users\dcjam\AppData\Local\Ethereum\keystore\UTC--2021-10-10T07-34-03.667044900Z--e51d1ad2afd68a71a04b6ecd8efb0c522f032fb9
``` 

- 키는 기본적으로 `--datadir` 경로 내에 저장되며 `--keystore` 옵션을 사용해 다를 경로를 지정할 수 있습니다. 