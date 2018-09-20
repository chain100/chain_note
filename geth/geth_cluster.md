
本地搭建geth集群环境

* 必须用同相同的genesis.json来初始化
* networkid 必须相同

# genesis.json 内容如下

```
{
   "config": {
        "chainId": 12345,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
    "coinbase" : "0x0000000000000000000000000000000000000000",
    "difficulty" : "0x01",
    "extraData" : "0x123456",
    "gasLimit" : "0xffffffff",
    "nonce" : "0x0000000000000042",
    "mixhash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "timestamp" : "0x00",
    "alloc": { }
}

```
# 创建节点01
* node01 node02

* geth --datadir=./node01 init ./node01/genesis.json

* geth --identity "test" --rpc --rpccorsdomain "*" --datadir /chain/geth_cluster/node01 --port "30301" --nodiscover --rpcport 8101 --rpcapi "db,eth,net,web3" --networkid 2018 

* admin.nodeInfo 

复制 node 信息

# 创建节点02

* geth --datadir=./node02 init ./node02/genesis.json

* geth --identity "test" --rpc --rpccorsdomain "*" --datadir /chain/geth_cluster/node02 --port "30302" --nodiscover --rpcport 8102 --rpcapi "db,eth,net,web3" --networkid 2018 

* admin.addPeer("node01-nodeInfo") // 粘贴node01的nodeInfo信息

* net.peerCount 显示为1

* admin.peers 显示节点完整信息



