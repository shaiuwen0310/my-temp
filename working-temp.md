## 序列化api的request及response
* 先調整cc, 只回value不組欄位
* 透過1u條列出目前的request及response
* orderform的response會有那些欄位?
```js
class MyClass {
  constructor(name, age, sex) {
    this.name = name,
    this.age = age,
    this.sex = sex
  }
}

var myClass = new MyClass("judy", 28, "female")

console.log(JSON.stringify(myClass));
```
結果: 
```json
{
    "name": "judy",
    "age": 28,
    "sex": "female"
}
```

## 外部构建器和启动器-and-将链码作为外部服务
* 自定義peer-image或外掛"External builder and launcher API"
* fabric2.4對於外部鍊碼更為強調
* k8s適合
* 2.2範例沒有tls, 要另外找: [文章1](https://arsulegai.medium.com/hyperledger-fabric-tls-enabled-external-chaincode-bcbab5618740)
* 2.2只有go合約可以用, 若有tls也需要再合約設置
* 合約要增加使用shim.ChaincodeServer API
* [整個流程的範例文章](https://medium.com/@robinklemens/setting-up-the-external-chaincode-builder-and-launcher-in-hyperledger-fabric-2-0-b17f43a3d8ed)
* 外部鍊碼失敗,會退回原本打包流程,我們應該是不讓他退回去?
* **我們要打包節點嗎?還是照樣用預設的,有外部東西直接外掛?**
* [asset-transfer-basic/chaincode-external](https://github.com/hyperledger/fabric-samples/tree/release-2.2/asset-transfer-basic/chaincode-external)
* [External Chaincode Launcher - Hyperledger Fabric](https://saifworks.hashnode.dev/external-chaincode-launcher-hyperledger-fabric)
