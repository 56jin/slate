# Core 模块

## Product Index

### URL

`POST   /core/product/index`

获取放在首页的产品


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": [
    {
        "id": null,
        "name": "海富货A",
        "type": "FP.PRODUCT.TYPE.1",
        "typeDesc": "基金",
        "code": "519505",
        "category": "MONETARY",
        "categoryDesc": null,
        "group": "FP.RECOMMEND.TYPE.1",
        "groupDesc": "首页",
        "tag": "FP.RECOMMEND.FLAG.1",
        "tagDesc": "荐",
        "peopleOfPurchased": 36894,
        "sevenDaysIncome": "0.0393",
        "millionIncome": "1.0387",
        "purchasedMethod": "随买随卖",
        "purchasedAmount": "100",
        "discount": "免手续费",
        "activity": "",
        "purchaseState": 1
    }
]}
```
    
## Product List

### URL

`POST   /core/products`

获取产品列表 
    
### Parameters

`Form格式： index=0&pageSize=10&category= STF&type=FP.PRODUCT.TYPE.1`

type:

值                  |       描述 
---------           | ----------- 
FP.PRODUCT.TYPE     |	产品类型
FP.PRODUCT.TYPE.1	|	基金
FP.PRODUCT.TYPE.2	|	票据 
FP.PRODUCT.TYPE.3	|	P2P 
FP.PRODUCT.TYPE.4	|	银行资管  

category:

值          |    描述 
---------   | ----------- 
ALL 	    |   显示所有基金
OPEN 	    |   开放式基金（fundtype为2的基金，排除货币、短期理财、QDII、创新型）
BOND	    |   债券型基金
INDEX       |   指数型基金
STOCK       |   股票型
QDII        |   QDII	
GUARANTEED	|   保本型(Guaranteed Captical)
INNOVATION  |   创新型
HYBIRD	    |   混合型
MONETARY    |	货币型(不含短期理财)
STF         |   短期理财(不含集合理财)(Short Term Financial Product)
CFP         |   集合理财(Collection Financial Product)

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": {
    "index": 0,
    "pageSize": 10,
    "pageNum": 0,
    "count": 1,
    "list": [
        {
            "id": null,
            "name": "大成21债A",
            "type": "FP.PRODUCT.TYPE.1",
            "typeDesc": "基金",
            "code": "090023",
            "category": "2",
            "categoryDesc": null,
            "group": "FP.RECOMMEND.TYPE.1",
            "groupDesc": "推荐",
            "tag": "FP.RECOMMEND.FLAG.2",
            "tagDesc": "抢",
            "peopleOfPurchased": 111,
            "sevenDaysIncome": "0.0354",
            "millionIncome": "0.9732",
            "purchasedMethod": "7天",
            "purchasedAmount": "1000",
            "discount": "免手续费",
            "activity": ""
        }
    ]
}}
```

## Product Detail

### URL

`POST        /core/product/detail`

### Parameters

`Form格式：type=FP.PRODUCT.TYPE.1&code=000009`

type:

值                  |  描述 
---------           | ----------- 
FP.PRODUCT.TYPE     |	产品类型
FP.PRODUCT.TYPE.1	|	基金
FP.PRODUCT.TYPE.2	|	票据 
FP.PRODUCT.TYPE.3	|	P2P 
FP.PRODUCT.TYPE.4	|	银行资管  

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": {
    "id": null,
    "name": "工银货币",                      
    "type": "FP.PRODUCT.TYPE.1",                  
    "typeDesc": "基金",                     
    "code": "482002",                      
    "category": "MONETARY",
    "categoryDesc": "货币型",
    "group": "FP.RECOMMEND.TYPE.2",
    "groupDesc": "其他",
    "tag": "FP.RECOMMEND.FLAG.3",
    "tagDesc": "热",
    "peopleOfPurchased": 36557,
    "sevenDaysIncome": "0.0404",
    "millionIncome": "1.0460",
    "purchasedMethod": "随买随卖",
    "purchasedAmount": "100",
    "discount": "免手续费",
    "discountValue": "1.0000",
    "activity": null,
    "purchaseState": 1,
    "toAccountType": "快速赎回",
    "riskLevel": "低风险",
    "companyName": null,
    "fundScale": "1143.28亿",
    "buiersOf30Days": 5699,
    "currentDate": "2014-12-11",
    "establishmentDate": null,
    "latestHoldShares": null,
    "manager": null,
    "trusteeName": null
}}
```

## Product Chart

### URL

`POST /core/product/chart`

### Parameters

`chartType=1& prdCode=GYHB& interval=7`

值          |       描述 
---------   | ----------- 
chartType   | 1(万份收益走势); 2(七日年化)

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": {
    "prdName": "易方达天天B",
    "prdCode": "000010",
    "chartType": "1",
    "chartName": "万份收益走势",
    "points": [
        {
            "date": "2014-11-20",
            "value": "1.41440"
        },
        {
            "date": "2014-11-20",
            "value": "1.41440"
        }
    ]
}}
```

## Attention List

### URL 

`POST /core/product/attentions`

### Parameters

`index=0&pageSize=10`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": {
        "index": 0,
        "pageSize": 10,
        "pageNum": 0,
        "count": 1,
        "list": [
            {
                "id": null,
                "name": "海富货A",
                "type": "FP.PRODUCT.TYPE.1",
                "typeDesc": "基金",
                "code": "519505",
                "category": "7",
                "categoryDesc": null,
                "group": "FP.RECOMMEND.TYPE.1",
                "groupDesc": "推荐",
                "tag": "FP.RECOMMEND.FLAG.2",
                "tagDesc": "抢",
                "peopleOfPurchased": 36894,
                "sevenDaysIncome": "0.0476",
                "millionIncome": "1.0695",
                "purchasedMethod": "随买随卖",
                "purchasedAmount": "100.0000",
                "discount": "免手续费"
            }
        ]
    }}
```

消息编码    |   错误描述
---------  | ----------- 
0000	   |   操作成功
2401	   |   类型不能为空
2402	   |   产品详情查询失败
2403	   |   种类不能为空

## Attention Product 

### URL

`POST /core/product/attention/create`

### Parameters

`code=519505`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": null}
```

## Attention Products

### URL

`POST /core/product/attentions/create`

### Parameters

`Form格式:codes[2]=161608 codes[1]=202301,codes[0]=519505`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": null}
```

## Cancel Attention

### URL

`POST /core/product/attention/cancel`

### Parameters

`code=519505`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": null}
```

## Agreement

### URL

`POST /core/agreement/findlinkbycode`

### Parameters

`code=0001`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": {
        "title": "用户协议",
        "link": "http://192.168.1.97:8888/www/userinstructions.html",
        "updatedAt": "2014-09-27 12:04:58",
        "code": "0001"
    }}
```

## Deposit Interest Rate

### URL

`POST /core/deposit/interest/current`

> The above command returns JSON structured like this:

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": 0.0035}
```


## gen Verification Code

### URL
`POST /core/verificationcode`

### Parameters
`Form格式：mobilePhoneNo=13811599308&type=REGISTER&deviceNo=123`

type:

值                  |  描述
---------           | -----------
REGISTER            |	注册
RESETPWD	        |	忘记密码
RESETACCOUNT	    |	重置交易密码

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0000",
            "summary": "操作成功",
            "detail": "操作成功",
            "fileds": { }
        },
        "value": null
    }
```


## register

### URL
`POST /core/register`

### Parameters
`Form格式：mobilePhoneNo=13811599308&passWord=encrypt(MD5)&verifyCode=1234&deviceNo=123&recommendPhone=15821948594`

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0100",
            "summary": "注册成功",
            "detail": "",
            "fields": { }
        },
        "value": {
            "userName": null,
            "nickName": null,
            "mobilePhoneNo": "15821948586",
            "mobileDisplayNo": "158****8586",
            "email": null,
            "gestureOpened": "0",//0关闭、1开启
            "certify": "0",//0 未实名 1实名
            "idCardNo": null,
            "bankCardCount": "0",
            "tradePwdFlag": "0",//0未1已
            "gestureSetted": "0",//首次设置手势密码0是1否
            "shumi_tokenKey": null,
            "shumi_tokenSecret": null,
            "shumi_userName": null,
            "shumi_realName": null,
            "shumi_idNumber": null,
            "shumi_bankName": null,
            "shumi_bankCardNo": null,
            "shumi_bankSerial": null,
            "shumi_phoneNum": null,
            "shumi_email": null
        }
    }
```


消息编码    |   错误描述
---------  | -----------
0100	   |   注册成功
2001	   |   访问失败	参数为空
2101	   |   该手机号已注册
2103	   |   验证码不正确	请重新输入
2104	   |   验证码失效	请重新获取
2105	   |   未获取验证码	请获取验证码



## certify

### URL
`POST /core/certify`

### Parameters
`Form格式：mobilePhoneNo=13811599308&userName=name&idCardNo=111121212121234&deviceNo=123`

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0201",
            "summary": "认证成功",
            "detail": "",
            "fields": { }
        },
        "value": {
            "userName": null,
            "nickName": null,
            "mobilePhoneNo": "15821948586",
            "mobileDisplayNo": "158****8586",
            "email": null,
            "gestureOpened": "0",
            "certify": "0",
            "idCardNo": null,
            "bankCardCount": "0",
            "tradePwdFlag": "0",
            "gestureSetted": "0",
            "shumi_tokenKey": null,
            "shumi_tokenSecret": null,
            "shumi_userName": null,
            "shumi_realName": null,
            "shumi_idNumber": null,
            "shumi_bankName": null,
            "shumi_bankCardNo": null,
            "shumi_bankSerial": null,
            "shumi_phoneNum": null,
            "shumi_email": null
        }
    }
```

消息编码    |   错误描述
---------  | -----------
0201	   |   认证成功
2001	   |   访问失败	参数为空
2002	   |   登录超时	请重新登录
2201	   |   认证失败 	不一致/库中无此号
3200	   |   实名认证失败






## bankCard create

### URL
`POST /core/bank/bankcard/create`

### Parameters
`Form格式：bankName=name&bankCard=111121212121234&bankSerial=123`

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0210",
            "summary": "操作成功",
            "detail": "银行卡添加成功",
            "fileds": { }
        },
        "value": null
    }
```



## bankCard saveAll

### URL
`POST /core/bank/bankcard/saveall`

### Parameters
`Form格式：
    cards=[
           {
           "No": "912739172312333333", -->银行卡号
           "TradeAccount": "0299", -->基金交易账号
           "SubTradeAccount": "0299;", -->
           "IsVaild": true, -->卡是否已经通过验证
           "Balance": 0.0, -->每日额度限制，如果为0则说明没有限制
           "Status": "0", -->卡的状态
           "StatusToCN": "正常", -->卡状态对应的说明
           "IsFreeze": false, -->是否被冻结
           "BankSerial": "005", -->银行编号
           "BankName": "建设银行", -->银行名称
           "CapitalMode": "6", -->绑卡渠道
           "BindWay": "0", -->绑卡方式
           "SupportAutoPay": true, -->
           "DiscountRate": 0.40, -->购买时折扣
           "LimitDescribe": "单笔50万元，日累计50万元", -->限制描述
           "ContentDescribe": "必须开通网上银行(U盾或动态口令)" -->
           },
           ...
           ]
`

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0000",
            "summary": "操作成功",
            "detail": "",
            "fileds": { }
        },
        "value": null
    }
```