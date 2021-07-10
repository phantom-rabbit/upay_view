## rpc请求地址
+ [POST]
+ Content-Type: application/json  
+ http://localhost:1669/rpc/v0

## 充值回调 
+ 接收到回调请求后应当返回 SUCCESS，系统收到SUCCESS后将不再发起回调
+ 系统默认最大发送100次回调，1分钟一次。超过次数将不再回调，需要手动触发回调
+ 回调请求数据如下:
```
{
    "data":{
        "amount":"1.08", //充值金额
        "app_id":"TEST", 
        "chain":"Filecoin",
        "error":"", //充值失败信息描述
        "from":"f1f52jfxx7crkzmpxgs7oa76md33ba2ezeqrloo2q",
        "hash":"bafy2bzacebevlrwpgziubvus2xc2nog2ceanf63efi3lzl5smvzdoel7qv4ne",
        "success":false, //交易状态 成功=true，失败=false
        "symbol":"FIL", //代币符号
        "timestamp":1625843400, //链上交易时间
        "to":"f1752ajs2iho7upcjfscoeeet3w2mzfxj3tpwa4sy" //充值地址
    },
    "time":"2021-07-09 23:40:24" //回调时间
}
```

## 地址生成
+ 参数
    + appId string 配置文件配置的APP编号
    + chian string 例如Filcoin网络 传Filecoin

+ 示例
```
{
  "jsonrpc":"2.0",
  "method":"UPAY.NewAddress",
  "params":["AppID", "Filecoin"],
  "id":1
}
```
+ 返回
```
{
    "jsonrpc":"2.0",
    "result":"f1752ajs2iho7upcjfscoeeet3w2mzfxj3tpwa4sy", //地址
    "id":1
}
```

## 查询余额
+ 参数
  + chian   string 例如Filcoin网络就传Filecoin
  + symbol  string 代币名称
  + address string 地址

+ 示例
```
{
  "jsonrpc":"2.0",
  "method":"UPAY.GetBalance",
  "params":[
    {
      "chain": "Filecoin",
      "symbol": "Fil",
      "address": "f1xxtq2mhmlgsqbatndgdhfqutlmn7kwmk2dthl6q"
    }
  ],
  "id":1
}
```
+ 成功返回示例
```
{
    "jsonrpc":"2.0",
    "result":"3.060000000000000000", //金额
    "id":1
}
```

## 出款
+ 参数
  + appId string 配置文件配置的APP编号
  + chian string 例如Filcoin网络 传Filecoin
  + symbol string 代币名称
  + to    string  收款地址
  + value float   金额

+ 示例
```
{
  "jsonrpc":"2.0",
  "method":"UPAY.Drawing",
  "params":[
    {
      "chain": "Filecoin",
      "app_id": "TEST",
      "symbol": "FIL",
      "to": "f1xxtq2mhmlgsqbatndgdhfqutlmn7kwmk2dthl6q",
      "value": 1378
    }
  ],
  "id":1
}
```

+ 成功返回示例
```
{
    "jsonrpc":"2.0",
    "result":"bafy2bzaceb4i7sciu5yoiuu7jdvopvthxd5647hftegpuyruqyjj37rq72qvq", //交易哈希
    "id":1
}
```

+ 错误返回示例
```
{
    "jsonrpc":"2.0",
    "id":1,
    "error":{
        "code":1,
        "message":"estimating gas used: message execution failed: exit SysErrInsufficientFunds(6), reason: failed to transfer funds (RetCode=6): transfer failed when deducting funds (1378 FIL): not enough funds (RetCode=6)"
    }
}
```