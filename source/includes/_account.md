# Account 模块

## 数米用户回调（参数为数米SDK返回参数）

### URL
`POST /account/saveshumiaccount`

### Parameters
`Form格式：shumi_tokenKey;
          shumi_tokenSecret;
          shumi_userName;
          shumi_realName;
          shumi_idNumber;
          shumi_bankName;
          shumi_bankCardNo;
          shumi_bankSerial;
          shumi_phoneNum;
          shumi_email;`

 请求带token

> The above command returns JSON structured like this:


```json
    {
        "message": {
            "severity": 0,
            "code": "0217",
            "summary": "数米信息保存成功",
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