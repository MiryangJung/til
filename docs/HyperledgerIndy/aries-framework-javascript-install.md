---
layout: default
title: aries-framework-javascript Install
parent: HyperledgerIndy
---


> [hyperledger/aries-framework-javascript](https://github.com/hyperledger/aries-framework-javascript)

## 필수 요소

1. Node.js
2. Python3
3. [Libindy](#Libindy-설치)

### Libindy 설치

**Windows**

1. [repo.sovrin.org/windows/{library}/{release-channel}](https://repo.sovrin.org) 에서 다운로드
2. ??

**MacOS**

1. `brew tap blu3beri/homebrew-libindy`
2. `brew install libindy`

## 패키지 설치

```shell
npm install @aries-framework/core @aries-framework/node
```


## Troubleshooting

Error A
{: .label .label-red }

```shell
gyp: No Xcode or CLT version detected!
```

Solution A
{: .label .label-green }

```shell
sudo rm -rf /Library/Developer/CommandLineTools 
xcode-select --install
```

Error B
{: .label .label-red }

```shell
Library not loaded: /usr/local/opt/libsodium/lib/libsodium.18.dylib
```

Solution B
{: .label .label-green }

```shell
ln -s /usr/local/opt/libsodium/lib/libsodium.23.dylib /usr/local/opt/libsodium/lib/libsodium.18.dylib
```

Error C
{: .label .label-red }

```shell
Library not loaded: /usr/local/opt/openssl/lib/libssl.1.0.0.dylib
```

Solution C
{: .label .label-green }

```shell
curl https://raw.githubusercontent.com/Homebrew/homebrew-core/64555220bfbf4a25598523c2e4d3a232560eaad7/Formula/openssl.rb -o openssl.rb
brew install openssl.rb
ln -sfn /usr/local/Cellar/openssl@1.0/1.0.2t /usr/local/opt/openssl
```


## Refer
- https://github.com/hyperledger/aries-framework-javascript/blob/main/TROUBLESHOOTING.md