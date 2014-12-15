---
title: API Reference

language_tabs:
  - java
  - objective-C
  - javascript

includes:
  - common
  - core
  - account
  - customer
  - trade
  - errors

search: true
---

# 使用介绍

请大家把自己负责模块的API文档写到includes目录下对应的makedown文件里面。
具体的写法请参考demo.md文件。

# Demo

## Get All Kittens

```java
import com.kitt;

public static String getKitt(String params){
	return WS.get(params);
}
```
> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```
This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>


