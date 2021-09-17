## 波场链USDT 充值对接API

## 生成地址
POST http://localhost:9000/rpc/v0
Content-Type: application/json

{
  "jsonrpc":"2.0",
  "method":"Cuckoo-Pay.GetNewAddress",
  "params":["appidtest"],
  "id":1
}

###{
#    "jsonrpc":"2.0",
#    "result":{
#        "code":"success",
#        "message":"",
#        "data":{
#            "address":"TFcgEXXRz7Pv2YU7UtbTwMCHFWY71yxaQJ"
#        }
#    },
#    "id":1
#}
<> `2021-06-04T030600.200.txt`

### USDT出款(此接口会从出款地址转出，请确保出款地址手续费和USDT足够)
POST http://localhost:9000//rpc/v0
Accept: application/json

{
  "jsonrpc":"2.0",
  "method":"Cuckoo-Pay.TransferUsdt",
  "params":[
   {
    "to":"TU3yVzRaLYZJbkw45HxVZGYsgaWV6BwJLV",
    "amount":"0.1",
    "app_id":"222222"
   }
  ],
  "id":1
}

###{
#    "jsonrpc":"2.0",
#    "result":{
#        "code":"success",
#        "message":"",
#        "data":{
#            "amount":"0.1",
#            "from":"TCiUAp1XsVBnB1CiTrydYNB14ztGvQcDvM",
#            "hash":"d10117bfefced427f60281e4511ccad8be6b5b143efdef01ed8069fa50a2cec8",
#            "to":"TU3yVzRaLYZJbkw45HxVZGYsgaWV6BwJLV"
#        }
#    },
#    "id":1
#}

### 查询余额
POST http://localhost:9000//rpc/v0
Accept: application/json

{
  "jsonrpc":"2.0",
  "method":"Cuckoo-Pay.GetBalance",
  "params":[
    "TULoENvZh62DdrbHPFNAKBh7t2SibZDuop"
  ],
  "id":1
}

###{
#  "code": "success",
#  "message": "",
#  "data": {
#   "trx": 15.751671,
#   "usdt": 0.9
#  }
# }

###回调数据 返回 SUCCESS
#{
#    "data":{
#        "app_id":"2222222",
#        "amount":"0.1",
#        "from":"TCiUAp1XsVBnB1CiTrydYNB14ztGvQcDvM",
#        "hash":"da261d858d0854b2a77827313bf654cc28dbd9da2d69250a714ee35f1b19c60d",
#        "state":1,
#        "timestamp":1622747859000,
#        "to":"TU3yVzRaLYZJbkw45HxVZGYsgaWV6BwJLV"
#    },
#    "name":"USDT",
#    "time":"2021-06-04 03:18:57"
#}
