# Core 模块

## 产品首页

### URL

`POST   /core/product/index`

### 返回

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

### URL

`POST   /core/products`
    
### 参数

`Form格式： index=0&pageSize=10&category= STF&type=FP.PRODUCT.TYPE.1`

type:

值           |       描述 
--------- | ----------- 
FP.PRODUCT.TYPE |	产品类型
FP.PRODUCT.TYPE.1	|	基金
FP.PRODUCT.TYPE.2	|	票据 
FP.PRODUCT.TYPE.3	|	P2P 
FP.PRODUCT.TYPE.4	|	银行资管  

category:

值           |    描述 
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

### 返回

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

值           |       描述 
--------- | ----------- 
FP.PRODUCT.TYPE |	产品类型
FP.PRODUCT.TYPE.1	|	基金
FP.PRODUCT.TYPE.2	|	票据 
FP.PRODUCT.TYPE.3	|	P2P 
FP.PRODUCT.TYPE.4	|	银行资管  

### 返回

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

值           |       描述 
--------- | ----------- 
chartType| 1(万份收益走势); 2(七日年化)

### 返回

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





## 协议

POST        /product/detail                   
POST        /product/chart                   
POST        /product/index                    
POST        /products                         
POST        /product/attentions            
POST        /product/attention/create        
POST        /product/attentions/create       
POST        /product/attention/cancel

## 银行活期利率

### URL

`POST /core/deposit/interest/current`

### 返回

```json
    {"message": {
        "severity": 0,
        "code": "0000",
        "summary": "操作成功",
        "detail": "",
        "fields": {}
    }, "value": 0.0035}
```

    
