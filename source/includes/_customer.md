# customer 模块

## Activity List

### URL

`POST   /account/activity/list`

### Parameters

`Form格式： index=0&pageSize=10&filter=0`

filter:

值        |       描述
--------- | -----------
0         |	不需要过滤
1	      |	查询每个客户聚宝盆的活动


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0221",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
    "index": 0,
    "pageSize": 10,
    "count": 1,
    "list": [
        {
            "id": 2,
            "name": "送积分",
      		"image": " http://192.168.1.97:9443/assets/help/songjifen.png",
            "url": " http://192.168.1.97:9443/assets/help/login.html"
        }
    ]
}}
```


## Init Sign button

### URL

`POST   /account/reward/get_signin`

### Parameters

`request需要带token(放在Cookie里)`

status:

值        |       描述
--------- | -----------
N         |	开放
F	      |	关闭

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0221",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
	"scene":"ASC001",
    "status":"N",
	"alreadyGet" :0,
	"notGet" :50
}}
```

## Sign obtain reward

### URL

`POST   /account/activity/signin`

### Parameters
`request需要带token(放在Cookie里)`
`Form格式： scene=ASC001`

scene:

值        |       描述
--------- | -----------
ASC001    |	签到场景


> The above command returns JSON structured like this:

```json
返回（签到成功）
{"message": {
    "severity": 0,
    "code": "0220",
    "summary": "签到成功",
    "detail": "",
    "fields": {}
}, "value": {
    "scene":"ASC001",
    "status":"F",
	"alreadyGet" :50,
	"notGet" :0
}}

返回（签到失败--重复签到）
{"message": {
    "severity": 0,
    "code": "2220",
    "summary": "当天不能重复签到",
    "detail": "",
    "fields": {}
}, "value": {
    "scene":"ASC001",
    "status":"F",
	"alreadyGet" :50,
	"notGet" :0
}}
```

## My golden bean details

### URL

`POST   /account/reward/get_golden`

### Parameters
`request需要带token(放在Cookie里)`



> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0222",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
    "totalReward": 162,
	"totalCash": 16.10,
	"redPacket": 161.00,
	" gots ": +162,
	" payed ": -162,
	"ruleUrl":"http://192.168.1.97/activity/signin.html"
    " records ": [
        {
            "createTime":"2014-11-18 08:57:28",
			"title":"分享到微信朋友圈",
			"amount":"+100"
        }
		{
            "createTime":"2014-11-18 08:57:28",
			"title":"兑换工银货币",
			"amount":"-100"
        }
    ]
}}
```

## register obtain reward

### URL

`POST   /account/activity/register`

### Parameters
`request需要带token(放在Cookie里)`

status:

值        |       描述
--------- | -----------
N         |	开放
F	      |	关闭


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0220",
    "summary": "获取金豆成功",
    "detail": "",
    "fields": {}
}, "value": {
    "scene":"ASC004",
    "status":"F",
	"alreadyGet" :50,
	"notGet" :0
}}

```


## trade obtain reward

### URL

`POST   /account/activity/trade`


### Parameters
`request需要带token(放在Cookie里)`
`Form格式： tradeType=0&fundCode=10&supplySum= 20.00`

tradeType:

值        |       描述
--------- | -----------
0         |	申购
1	      |	赎回

rewardType:

值        |       描述
--------- | -----------
ART00J    |	送金豆
ART00H	  |	送红包


> The above command returns JSON structured like this:

```json
返回（成功）
{"message": {
    "severity": 0,
    "code": "0220",
    "summary": "获取金豆成功",
    "detail": "",
    "fields": {}
}, "value": {
	"fundCode":"30078",
	"supplySum":"200.00",
    " records ": [
        {
			"title":"购买送红包",
			"rewardType":"ART00H",
			"detail":"20元红包",
			"ruleUrl":" http://192.168.1.97:9443/assets/help/login.html"
        }
		{
			"title":"购买送红包",
			"rewardType":"ART00H",
			"detail":"20元红包",
			"ruleUrl":" http://192.168.1.97:9443/assets/help/login.html"
	     }
    ]
}}
返回失败情况：
{"message": {
    "severity": 0,
    "code": "2221",
    "summary": "获取金豆失败",
    "detail": "没有配置活动场景",
    "fields": {}
}, "value": {
	"fundCode":"30078",
	"supplySum":"200.00"
}}
```


## share

### URL

`POST   /customer/activity/share`

### Parameters
`Form格式： type=0&id=10`

type:

值        |       描述
--------- | -----------
0         |	分享app(需要登录)
1	      |	分享产品
2         |	分享收益
3	      |	分享活动


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0223",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
	"title":"分享"
	"content":"欢迎你的到来！",
    "shorturl":" http://t.cn/RzXKWQR ",
    "imageurl":"http://192.168.1.97/activity/images/loggon_icon.png",
	"type":"1",
	"id":"1111"
}}
```

## exchange scene list

### URL

`POST   /account/activity/exchangescenes`

### Parameters
`request需要带token(放在Cookie里)`


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0225",
    "summary": "兑换场景查询成功",
    "detail": "",
    "fields": {}
}, "value": {
    "index": 0,
    "pageSize": 10,
    "count": 1,
    "list": [
        {
            "id": 2,
            "title": "首次购买送红包",
      		"detail": "首次购买送红包20元",
            "logo": " http://192.168.1.97/activity/images/loggon_icon.png"
        }
		{
            "id": 3,
            "title": "购买理财产品送+4%收益",
      		"detail": "购买理财产品送+4%收益",
            "logo": " http://192.168.1.97/activity/images/loggon_icon.png"
        }
    ]
}}
```


## prepare data before exchange

### URL

`POST   /account/activity/beforeexchange`


### Parameters
`request需要带token(放在Cookie里)`
`Form格式： id=123`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0226",
    "summary": "兑换前预准备成功",
    "detail": "",
    "fields": {}
}, "value": {
    "canPayed": 361.00,
    "maxPayed": 361.00,
    "accountDate": "2014-12-16 12:00:00",
	"summary": "首次购买20元",
    "list": [
        {
            "title": "首次购买送红包",
      		"detail": "首次购买送红包20元",
            "logo": " http://192.168.1.97/activity/images/loggon_icon.png"
			"createTime" : "2014-12-16 12:00:00"
        }
		{
            "title": "购买理财产品送+4%收益",
      		"detail": "购买理财产品送+4%收益",
            "logo": " http://192.168.1.97/activity/images/loggon_icon.png"
			"createTime" : "2014-12-16 12:00:00"
        }
    ]
}}
```

##exchange reward

### URL

`POST   /account/activity/exchange`


### Parameters
`request需要带token(放在Cookie里)`
`Form格式： id=123`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0227",
    "summary": "兑换成功",
    "detail": "您本次取现100元到光大银行，将在2014-16-17号收到",
    "fields": {}
}, "value": {
    "payed": 100.00,
    "accountDate": "2014-12-16 12:00:00"
}}

失败返回
{"message": {
    "severity": 0,
    "code": " 2228",
    "summary": "兑换数量不足",
    "detail": "抱歉，兑换数量不足",
    "fields": {}
}, "value": {

}}
```