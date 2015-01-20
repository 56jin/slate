# Trade 模块


## 申购回调（参数为数米SDK返回参数）

### URL
`POST /trade/shumitradeorder`

### Parameters
`Form格式：applySerial;
          fundCode;
          fundName;
          applySum;
          bankCardInfo;
          dateTime;
          bankName;
          bankAcco;`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0400",
            "summary": "下单成功",
            "detail": "",
            "fileds": { }
        },
        "value": null
    }
```

## 赎回回调（参数为数米SDK返回参数）

### URL
`POST /trade/shumitraderedeem`

### Parameters
`Form格式：applySerial;
          fundCode;
          fundName;
          applySum;
          bankCardInfo;
          dateTime;`

 请求带token

> The above command returns JSON structured like this:

```json
    {
        "message": {
            "severity": 0,
            "code": "0401",
            "summary": "赎回成功",
            "detail": "",
            "fileds": { }
        },
        "value": null
    }
```