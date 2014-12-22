# Trade 模块


## shumi trade order

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

## shumi trade redeem

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