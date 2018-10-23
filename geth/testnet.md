* eth区块浏览器

https://etherscan.io/

* rinkeby POA获取eth

https://rinkeby.etherscan.io/address/0x08511E760c5Dd3871eC7e8cde740f4780221e16F

* eth水龙头

https://faucet.rinkeby.io/

发一个推特内容为eth钱包地址，复制比推特链接地址获取eth币

* geth本地测试节点

```
geth --datadir /chain/geth_rinkeby --rinkeby --syncmode full --rpc console 2>/chain/geth_rinkeby/out.log
```

> eth.syncing

```
{
  currentBlock: 17796,
  highestBlock: 3209197,
  knownStates: 0,
  pulledStates: 0,
  startingBlock: 0
}
```

当eth.syncing返回false说明同步完成，要等同步完成后才能进行账户余额查询和转账的操作

参考资料

https://www.jianshu.com/p/e69d00c59c95

https://blog.csdn.net/wlhdo71920145/article/details/80418321
