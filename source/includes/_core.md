# Core 模块

## 产品首页

### HTTP 请求

`POST   /core/product/index`

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

    
## 产品列表

### HTTP 请求

`POST   /core/products`
    
### 参数

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

## 产品详情

### URL

`POST        /core/product/detail`

### 参数

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
    "id": 3360,
    "name": "工银货币",
    "type": "FP.PRODUCT.TYPE.1",
    "typeDesc": "基金",
    "code": "GYHB",
    "category": "FP.PRODUCT.TYPE.1.1",
    "categoryDesc": "货币型",
    "group": "FP.RECOMMEND.TYPE.1",
    "groupDesc": "推荐",
    "tag": "FP.RECOMMEND.FLAG.1",
    "tagDesc": "首页",
    "peopleOfPurchased": 30000,
    "sevenDaysIncome": 0.08,
    "millionIncome": 1.2654,
    "purchasedMethod": "随存随取",
    "purchasedAmount": 1,
    "toAccountType": "实时到账（T+0)",
    "riskLevel": "1R",
    "companyName": "好买基金",
    "fundScale": "190.10亿",
    "buiersOf30Days": 3000,
    "currentDate": "2014-11-18"
    }
}
```

## 图表

### URL

`POST /core/product/chart`

### 参数

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

##关注列表

### URL 

`POST /core/product/attentions`

###参数

`index=0&pageSize=10`

###返回

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

## 产品关注

### URL

`POST /core/product/attention/create`

### 参数

`code=519505`

### 返回

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

## 批量关注

### URL

`POST /core/product/attentions/create`

### 参数

`Form格式:codes[2]=161608 codes[1]=202301,codes[0]=519505`

### 返回

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

## 取消关注

### URL

`POST /core/product/attention/cancel`

### 参数

`code=519505`

### 返回

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

## 协议

### URL

`POST /core/agreement/findlinkbycode`

### 参数

`code=0001`

### 返回

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

## 银行活期利率

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

    
