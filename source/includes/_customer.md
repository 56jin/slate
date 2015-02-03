# customer 模块

## 活动列表
![“金品”中的滚动的活动页面](./activity/activityList.png)
![活动列表](./activity/activityCenter.PNG)
![“财富”中的我的金豆的豆荚中的活动列表](./activity/doujia.png)

### 说明：提供给“金品”中的滚动的活动页面用；也提供给“更多”中的活动中心页面用；也提供给“财富”中的我的金豆的豆荚中的活动列表

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
            "id": 2,       活动主键
            "name": "送积分",      活动名称
      		"image": " http://192.168.1.97:9443/assets/help/songjifen.png",          活动图片url
            "url": " http://192.168.1.97:9443/assets/help/login.html"                活动详情h5页面url
        }
    ]
}}
```


## 初始化签到按钮

![初始化签到按钮](./activity/mygolden.png)

### 说明：判断“财富”中的签到按钮是否置成不可用，如果状态返回N的话则该客户今天不能签到，否则今天可以签到

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
	"scene":"ASC001",   活动场景
    "status":"N",       状态
	"alreadyGet" :0,    已经获取奖励数量
	"notGet" :50        还没有获取奖励的数量
}}
```

## 签到获取奖励

![签到按钮](./activity/mygolden.png)

### 说明：“财富”中签到获取奖励的接口，获取多少接口可以在后台配置

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
    "scene":"ASC001",    活动场景
    "status":"F",         状态 N表示开放  F表示关闭
	"alreadyGet" :50,     已经获取奖励数量
	"notGet" :0           还没有获取奖励的数量
}}

返回（签到失败--重复签到）
{"message": {
    "severity": 0,
    "code": "2220",
    "summary": "当天不能重复签到",
    "detail": "",
    "fields": {}
}, "value": {
    "scene":"ASC001",       活动场景
    "status":"F",           状态 N表示开放  F表示关闭
	"alreadyGet" :50,       已经获取奖励数量
	"notGet" :0             还没有获取奖励的数量
}}
```

## 奖励详情

![奖励详情](./activity/goldenxiangqing.png)

### 提供给“财富”中的我的金豆荚的查询接口；也提供给“财富”--》我的金豆的详细页面查询所需的接口

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
    "totalReward": 162,     总金豆
    "totalCash": 16.10,     金豆对应的金额
    "redPacket": 161.00,    红包数量
    "ruleUrl":"http://192.168.1.97/activity/signin.html"    规则h5页面

}}
```

## 奖励流水记录

![奖励流水记录](./activity/record.PNG)

### 供给“财富”--》我的金豆中的“记录”tab的记录

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
			"title":"分享到微信朋友圈",         参加活动名称
			"amount":"+100"                     流水数量
            "createTime":"2014-11-18 08:57:28", 创建时间
			"status":"成功"                       状态
			"rewardType":"0"                   //0 红包 1 金豆
        },
        {
            "title": "金豆兑换10元话费",
            "amount": "-1000",
            "createTime": "2015-02-03 11:12:02",
            "status": "兑换中",
            "rewardType": "1"
        },
		{
			"title":"兑换工银货币",
			"amount":"-100"
            "createTime":"2014-11-18 08:57:28",
			"status":"成功"
			"rewardType":"0"
        }
    ]
}}

```

## 注册送金豆

## 前端注册成功后触发这个接口可以送金豆给注册的客户

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
    "scene":"ASC004",  活动场景
    "status":"F",       状态 N表示开放  F表示关闭
	"alreadyGet" :50,   已经获取奖励数量
	"notGet" :0             还没有获取奖励的数量
}}

```


## 首次购买送红包(后台触发)

## 这个接口前端不需要触发，是在后台的购买流程里会触发的

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
			"title":"购买送红包",     标题
			"rewardType":"ART00H",      奖励类型
			"detail":"20元红包",       描述信息
			"ruleUrl":" http://192.168.1.97:9443/assets/help/login.html"    规则url
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


## 分享接口

## 为分享活动而准备数据的接口

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

## 兑换场景列表

### 给“财富”中的我的金豆的兑换tab提供查询接口

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


## 兑换动作前的准备数据的接口

### 在“财富”中的我的金豆中的兑换前准备数据接口

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


##金豆兑换话费前准备数据

### URL

`POST   /account/activity/beforebeanexchange`


### Parameters
`request需要带token(放在Cookie里)`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": "0229",
    "summary": "金豆兑换前预准备成功",
    "detail": "",
    "fields": {}
}, "value": {
    "rate": "0.01",
    "exchangeList": [
        "10",
        "20",
        "50",
        "100",
        "200",
        "500"
    ]
}}
```



##exchange reward

### 兑换动作实现

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



### Parameters（金豆兑换）
`request需要带token(放在Cookie里)`
`Form格式： id=123&phone="12321111111"&amount=20.03`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0227",
    "summary": "兑换成功",
    "detail": "",
    "fields": {}
}, "value": null
}

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



##获取该活动剩余发放数量

### URL

`GET   /account/activity/remain/:id `


### Parameters

`id为活动id`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": 40
}

```


##判断该活动是否已结束

### URL

`GET  /activity/isover/:id  `


### Parameters

`id为活动id,返回true已结束，false未结束`

> The above command returns JSON structured like this:

```json
{"message": {
    "severity": 0,
    "code": " 0000",
    "summary": "操作成功",
    "detail": "",
    "fields": {}
}, "value": true
}

```

## 登录

![登录](./login.png)

### URL
`POST /customer/login`

### Parameters
`Form格式：mobilePhoneNo=13811599308&passWord=123222&deviceNo=123`

 request需要带token(放在Cookie里)

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



## 手势登录

![手势登录](./login_by_ges.png)

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



## 重置密码验证

![未实名重置密码验证](./reset_pwd_certify.png)
![实名重置密码验证](./reset_pwd_certify2.png)

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



## 重置密码

![重置密码](./reset_pwd.png)

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



## 密码确认

![密码确认](./confirm_pwd.png)

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


## 保存关闭手势密码

![密码确认](./save_gesture_pwd.png)

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




## 退出登录

![退出登录](./logout.png)

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




## 用户查询

![用户查询](./get_user_info.png)

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


## 反馈

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


## 消息查询

![消息查询](./message_list.png)

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
                       "msgId": 216627,                                                     消息ID
                       "messageRuleId": 6,                                                  消息规则ID
                       "title": "红包取现",                                                  标题
                       "summary": "尊敬的用户，您申请取现红包0.01元成功，我们工作人员将在1...",   概要
                       "createTime": "2014-12-23 08:40",                                    创建时间
                       "sendType": "FP.SEND.TYPE.3",                                        推送类型
                       "readInd": "N"                                                       阅读标志 Y已阅读 N未
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





## 查看消息明细

![查看消息明细](./message_detail.png)

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



## 未读记录数量查询

![未读记录数量查询](./count_un_read_num.png)

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



## 推送开启

### URL
`POST /customer/message/enablepush`

### Parameters

request header(name = "DeviceNo", value = 设备号)
request header(name = "registrationId", value = 调用JPush SDK返回的)

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0218",
            "summary": "推送开启成功",
            "detail": "",
            "fields": { }
        },
        "value": null
    }
```



## 推送关闭

### URL
`POST /customer/message/disablepush`

### Parameters

request header(name = "DeviceNo", value = 设备号)
request header(name = "registrationId", value = 调用JPush SDK返回的)

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0219",
            "summary": "推送关闭成功",
            "detail": "",
            "fields": { }
        },
        "value": null
    }
```





