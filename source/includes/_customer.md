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
    "ruleUrl":"http://192.168.1.97/activity/signin.html"

}}
```

## reward flow record

### URL

`POST   /account/reward/records`

### Parameters
`request需要带token(放在Cookie里)`
`Form格式： index=0&pageSize=10`


> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0228",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
	"index": 0,
    "pageSize": 10,
    "count": 2,
    " list ": [
        {
            "createTime":"2014-11-18 08:57:28",
			"title":"分享到微信朋友圈",
			"amount":"+100"
			"状态":"成功"
        }
		{
            "createTime":"2014-11-18 08:57:28",
			"title":"兑换工银货币",
			"amount":"-100"
			"状态":"成功"
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
`Form格式： index=0&pageSize=10`

exchangeType:

值        |       描述
--------- | -----------
0         |	兑换红包
1	      |	兑换话费
2         |	兑换Q币


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
      		"exchangeType": "0",
            "logo": " http://192.168.1.97/activity/images/loggon_icon.png"
        }
		{
            "id": 3,
            "title": "购买理财产品送+4%收益",
      		"detail": "购买理财产品送+4%收益",
      		"exchangeType": "0",
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
`Form格式： id=123&bankName="招商银行"&bankCode="CMB"&bankCard="2323232222"&phone="12321111111"&amount=20.03`

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


##get activity rule content

### URL

`POST   /account/activity/rule`


### Parameters

`Form格式： activityId=123`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0227",
    "summary": "查询成功",
    "detail": "",
    "fields": {}
}, "value": {
    "imageUrl": "http://192.168.1.97:9443/assets/help/songjifen.png",
    "content": "测试content"
}}

```


## login

### URL
`POST /customer/login`

### Parameters
`Form格式：mobilePhoneNo=13811599308&passWord=encrypt(MD5)&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0101",
            "summary": "登录成功",
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
0101	   |   登录成功
2001	   |   访问失败	参数为空
2002	   |   登录超时	请重新登录
2100	   |   该手机号未注册
2106	   |   密码错误次数过多	约xx分后再试
2107	   |   密码错误	剩余次数xx



## login by ges

### URL
`POST /customer/loginbyges`

### Parameters
`Form格式：mobilePhoneNo=13811599308&gesturePassWord=encrypt(MD5)&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0101",
            "summary": "登录成功",
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
0101	   |   登录成功
2001	   |   访问失败	参数为空
2002	   |   登录超时	请重新登录
2100	   |   该手机号未注册
2111	   |   未设置手势	请先开启手势
2109	   |   手势登录失败超过最大次数	请换密码登录
2108	   |   手势密码错误	剩余次数xx



## reset pwd certify

### URL
`POST /customer/resetpwdcertify`

### Parameters
`Form格式：mobilePhoneNo=13811599308&userName=name&idCardNo=4444444441211&verifyCode=1234&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0000",
            "summary": "操作成功",
            "detail": "操作成功",
            "fileds": { }
        }
    }
```

消息编码    |   错误描述
---------  | -----------
0000	   |   操作成功
2002	   |   登录超时	请重新登录
2001	   |   访问失败	参数为空
2103	   |   验证码不正确	请重新输入
2104	   |   验证码失效	请重新获取
2105	   |   未获取验证码	请获取验证码
2200	   |   真实姓名或身份证号错误



## reset pwd

### URL
`POST /customer/resetpwd`

### Parameters
`Form格式：mobilePhoneNo=13811599308&passWord=encrypt(MD5)&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0101",
            "summary": "登录成功",
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



## confirm pwd

### URL
`POST /customer/confirmpwd`

### Parameters
`Form格式：mobilePhoneNo=13811599308&passWord=encrypt(MD5)`

 请求带token

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


## save ges pwd

### URL
`POST /customer/savegespwd`

### Parameters
`Form格式：mobilePhoneNo=13811599308&gesturePassWord=encrypt(MD5)&gestureOpened=0&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0101",
            "summary": "登录成功",
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




## logout

### URL
`POST /customer/logout`

### Parameters
`Form格式：mobilePhoneNo=13811599308&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0104",
            "summary": "登出成功",
            "detail": "",
            "fileds": { }
        },
        "value": null
    }
```




## get usermstr

### URL
`POST /customer/getusermstr`

### Parameters
`Form格式：mobilePhoneNo=13811599308&deviceNo=123`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0000",
            "summary": "操作成功",
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


## add feedback

### URL
`POST /customer/addfeedback`

### Parameters
`Form格式：mobile=13811599308&deviceNo=123&feedback=这是内容`

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


## Search Message List

### URL
`POST /customer/message/list`

### Parameters
`Form格式：index=3&pageSize=5`

request带token 查询登录后的  未带查询登录前的
request header(name = "DeviceNo", value = 设备号)


sendType:

值              |       描述
--------------  | -----------
FP.SEND.TYPE.1  |	短信发送
FP.SEND.TYPE.2  |	群发推送
FP.SEND.TYPE.3  |	个人推送

readInd:

值     |    描述
------ | -----------
N      |	未读
Y      |	已读

> The above command returns JSON structured like this:

```json
    {
       {
           "message": {
               "severity": 0,
               "code": "0000",
               "summary": "操作成功",
               "detail": "",
               "fields": { }
           },
           "value": {
               "index": 3,
               "pageSize": 5,
               "pageNum": 0,
               "count": 7,
               "list": [
                   {
                       "msgId": 216627,
                       "messageRuleId": 6,
                       "title": "红包取现",
                       "summary": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1...",
                       "createTime": "2014-12-23 08:40",
                       "sendType": "FP.SEND.TYPE.3",
                       "readInd": "N"
                   },
                   {
                       "msgId": 216626,
                       "messageRuleId": 6,
                       "title": "红包取现",
                       "summary": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1...",
                       "createTime": "2014-12-23 08:40",
                       "sendType": "FP.SEND.TYPE.3",
                       "readInd": "N"
                   },
                   {
                       "msgId": 216625,
                       "messageRuleId": 6,
                       "title": "红包取现",
                       "summary": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1...",
                       "createTime": "2014-12-23 08:40",
                       "sendType": "FP.SEND.TYPE.3",
                       "readInd": "N"
                   },
                   {
                       "msgId": 216624,
                       "messageRuleId": 6,
                       "title": "红包取现",
                       "summary": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1...",
                       "createTime": "2014-12-23 08:39",
                       "sendType": "FP.SEND.TYPE.3",
                       "readInd": "N"
                   },
                   {
                       "msgId": 216623,
                       "messageRuleId": 5,
                       "title": "首次购买成功",
                       "summary": "尊敬的用户，恭喜您完成了首次购买，【金豆荚】赠送您20元红包...",
                       "createTime": "2014-12-23 08:34",
                       "sendType": "FP.SEND.TYPE.3",
                       "readInd": "N"
                   }
               ],
               "filter": { }
           }
       }
    }
```





## Search Message detail

### URL
`POST /customer/message/detail`

### Parameters
`Form格式：msgId=216623&sendType=FP.SEND.TYPE.3`

request带token
request header(name = "DeviceNo", value = 设备号)

> The above command returns JSON structured like this:

```json
    {
       {
           "message": {
               "severity": 0,
               "code": "0000",
               "summary": "操作成功",
               "detail": "",
               "fields": { }
           },
           "value": {
               "title": "红包取现",
               "content": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1个工作日内将现金打到您的银行卡里，请耐性等待。若逾期未到账请及时联系【金豆荚】的官方客服400-728-0153。【金豆荚】祝您理财愉快！",
               "createTime": "2014-12-23 08:40"
           }
       }
    }
```



## Search Message unreadnum

### URL
`POST /customer/message/unreadnum`

### Parameters

request带token
request header(name = "DeviceNo", value = 设备号)

> The above command returns JSON structured like this:

```json
    {
       {
           "message": {
               "severity": 0,
               "code": "0000",
               "summary": "操作成功",
               "detail": "",
               "fields": { }
           },
           "value": 5
       }
    }
```
