# Core 模块

## 产品首页

![首页接口v1.0](./product_index_v1.0.png)

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
}, "value": {
    "id": null,                          
    "name": "农银货币A",                        产品名称            
    "type": "FP.PRODUCT.TYPE.1",              产品类型
    "typeDesc": "基金",                        产品类型描述
    "code": "660007",                         产品代码
    "category": "MONETARY",                   产品种类
    "categoryDesc": "货币型",                  产品种类描述
    "group": "FP.RECOMMEND.TYPE.1",           组
    "groupDesc": "首页",                       组描述
    "tag": "FP.RECOMMEND.FLAG.1",             标志
    "tagDesc": "荐",                          标志描述
    "peopleOfPurchased": 272,                 购买人数
    "sevenDaysIncome": "0.0479",              七日年化
    "millionIncome": "1.3039",                万份收益
    "purchasedMethod": "随买随卖",              投资期限
    "purchasedAmount": "100",                 起购金额
    "discount": "免手续费",                     手续费描述
    "discountValue": "--",                    手续费
    "activity": "--",                         活动名称
    "purchaseState": 1                        是否可申购	1: 可申购 0:不可申购
}}
```
    
## 产品首页v2.0

![首页接口v2.0](./product_index_v2.0.png)

### URL

`POST   /core/v2.0/product/index`

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
            "name": "农银货币A",                        产品名称            
            "type": "FP.PRODUCT.TYPE.1",              产品类型
            "typeDesc": "基金",                        产品类型描述
            "code": "660007",                         产品代码
            "category": "MONETARY",                   产品种类
            "categoryDesc": "货币型",                  产品种类描述
            "group": "FP.RECOMMEND.TYPE.1",           组
            "groupDesc": "首页",                       组描述
            "tag": "FP.RECOMMEND.FLAG.1",             标志
            "tagDesc": "荐",                          标志描述
            "peopleOfPurchased": 272,                 购买人数
            "sevenDaysIncome": "0.0479",              七日年化
            "millionIncome": "1.3039",                万份收益
            "purchasedMethod": "随买随卖",              买卖方式
            "purchasedAmount": "100",                 起购金额
            "discount": "免手续费",                     手续费描述
            "discountValue": "--",                    手续费
            "activity": "--",                         活动名称
            "purchaseState": 1                        是否可申购	1: 可申购 0:不可申购
    }
]}
```
    
## 产品列表

![产品列表](./products.png)

### URL

`POST   /core/products`

获取产品列表 
    
### Parameters

`Form格式： index=0&pageSize=10&category=STF&type=FP.PRODUCT.TYPE.1`

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
    "count": 30,
    "list": [
        {
            "id": null,
            "name": "建信双月债A",                        产品名称
            "type": "FP.PRODUCT.TYPE.1",                产品类型
            "typeDesc": "基金",                          产品类型描述
            "code": "530029",                           产品代码
            "category": "STF",                          产品种类
            "categoryDesc": "短期理财",                   产品种类描述
            "group": "FP.RECOMMEND.TYPE.2",             组
            "groupDesc": "其他",                         组描述
            "tag": "FP.RECOMMEND.FLAG.2",               标志
            "tagDesc": "抢",                             标志描述
            "peopleOfPurchased": 208,                   购买人数
            "sevenDaysIncome": "0.0837",                七日年化
            "millionIncome": "1.0789",                  万份收益
            "purchasedMethod": "7天",                    投资期限
            "purchasedAmount": "100",                   起购金额
            "discount": "免手续费",                       手续费描述
            "discountValue": "--",                      手续费
            "activity": "--",                           活动名称
            "purchaseState": 1                          是否可申购	1: 可申购 0:不可申购
        }
    ]
}}
```

## 产品详细

![产品详细](./product_detail.png)

获取产品详细

### URL

`POST        /core/product/detail`

### Parameters

`Form格式：type=FP.PRODUCT.TYPE.1&code=530029`

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
    "name": "建信双月债A",                        产品名称
    "type": "FP.PRODUCT.TYPE.1",                产品类型
    "typeDesc": "基金",                          产品类型描述
    "code": "530029",                           产品代码
    "category": "STF",                          产品种类
    "categoryDesc": "短期理财",                   产品种类描述
    "group": "FP.RECOMMEND.TYPE.2",             组
    "groupDesc": "其他",                         组描述
    "tag": "FP.RECOMMEND.FLAG.2",               标志
    "tagDesc": "抢",                             标志描述
    "peopleOfPurchased": 208,                   购买人数
    "sevenDaysIncome": "0.0837",                七日年化
    "millionIncome": "1.0789",                  万份收益
    "purchasedMethod": "7天",                    投资期限
    "purchasedAmount": "100",                   起购金额
    "discount": "免手续费",                       手续费描述
    "discountValue": "--",                      手续费
    "activity": "--",                           活动名称
    "purchaseState": 1                          是否可申购	1: 可申购 0:不可申购
    "toAccountType": "普通赎回",                  取现到帐
    "riskLevel": "中风险",                        风险
    "companyName": "建信",                        基金公司名字
    "fundScale": "12.85亿",                      基金规模
    "buiersOf30Days": 204,                      30天购买人数
    "currentDate": "2015-01-12",                净值日期
    "establishmentDate": "2013-01-29",          成立日期
    "latestHoldShares": "795692386",            最新持有数
    "manager": "高珊",                            基金经理
    "trusteeName": "招商银行股份有限公司"           基金托管人
}}
```

## 产品图表

![产品详细](./product_detail.png)

获取产品列表

### URL

`POST /core/product/chart`

### Parameters

`chartType=1&prdCode=GYHB&interval=7`

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
    "prdName": "易方达天天B",                产品名称
    "prdCode": "000010",                   产品代码
    "chartType": "1",                      图表类型
    "chartName": "万份收益走势",             图标名称
    "points": [
        {
            "date": "2014-11-20",          净值日期
            "value": "1.41440"             万分收益/七日年化
        },
        {
            "date": "2014-11-20",
            "value": "1.41440"
        }
    ]
}}
```

## 关注列表

获取关注列表

### URL 

`POST /core/product/attentions`

### Parameters

`codes[0]=000009&codes[1]=000037`

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
        "pageSize": 0,
        "pageNum": 0,
        "count": 0,
        "list": [
            {
                "id": null,
                "name": "易方达天天A",
                "type": "FP.PRODUCT.TYPE.1",
                "typeDesc": "基金",
                "code": "000009",
                "category": "MONETARY",
                "categoryDesc": "货币型",
                "group": "FP.RECOMMEND.TYPE.2",
                "groupDesc": "其他",
                "tag": "FP.RECOMMEND.FLAG.2",
                "tagDesc": "抢",
                "peopleOfPurchased": 246,
                "sevenDaysIncome": "0.0501",
                "millionIncome": "1.7035",
                "purchasedMethod": "随买随卖",
                "purchasedAmount": "100",
                "discount": "免手续费",
                "discountValue": "--",
                "activity": "--",
                "purchaseState": 1
            },
            {
                "id": null,
                "name": "广发7天债A",
                "type": "FP.PRODUCT.TYPE.1",
                "typeDesc": "基金",
                "code": "000037",
                "category": "STF",
                "categoryDesc": "短期理财",
                "group": "FP.RECOMMEND.TYPE.2",
                "groupDesc": "其他",
                "tag": "FP.RECOMMEND.FLAG.2",
                "tagDesc": "抢",
                "peopleOfPurchased": 281,
                "sevenDaysIncome": "0.0492",
                "millionIncome": "1.3471",
                "purchasedMethod": "7天",
                "purchasedAmount": "1000",
                "discount": "免手续费",
                "discountValue": "--",
                "activity": "--",
                "purchaseState": 1
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
2404	   |   产品代码不能为空

## 协议

获取协议

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
        "title": "用户协议",                                                协议名称
        "link": "http://192.168.1.97:8888/www/userinstructions.html",      协议链接
        "updatedAt": "2014-09-27 12:04:58",                                更新时间
        "code": "0001"                                                     协议编号
    }}
```

## 银行活期

![银行活期](./deposit_interest.png)

获取银行活期

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
    }, "value": 0.0035}                                                   活期利率
```


## 获取验证码

![登录](./register.png)

### URL
`POST /core/verificationcode`

### Parameters
`Form格式：mobilePhoneNo=13811599308&type=REGISTER&deviceNo=123`

PS：(调用第二办公室短信发送接口，需通知对方绑定接口请求服务器IP地址)

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

![登录](./register.png)

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
            "userName": null,                            //真实姓名
            "nickName": null,                            //昵称
            "mobilePhoneNo": "15821948586",              //手机号
            "mobileDisplayNo": "158****8586",            //手机展示号
            "email": null,                               //邮箱
            "gestureOpened": "0",                        //手势密码状态： 0关闭、1开启
            "certify": "0",                              //实名认证状态： 0 未实名 1实名
            "idCardNo": null,                            //身份证号
            "bankCardCount": "0",                        //已绑卡数量
            "tradePwdFlag": "0",                         //是否设置了交易密码：0未1已
            "gestureSetted": "0",                        //是否是首次设置手势密码0是1否
            "shumi_tokenKey": null,                      //以下为数米返回信息
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

![登录](./register.png)

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