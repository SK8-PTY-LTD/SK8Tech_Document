旅淘淘新版数据库以及后台使用了[LeanCloud](https://leancloud.cn)作为后端解决方案，本文档详细介绍了数据类型，以及使用方法。

# 数据类型

数据库包括了以下“类”

  1. [Address](#Address)
  1. Comment 
  1. Moment 
  1. Recommendation 
  1. Quest 
  1. Order 
  1. Product 
  1. Transaction 
  1. _User

## Address

Address为用户保存的“收货地址”，键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|
| street1 |   true |String|  详细地址第一行|
|   street2 |      |String|   详细地址第二行   |
|   city   |   true |  String| 城市|
|   recipient|  true |   String|收件人|
|   contactNumber |  true |   String |手机号|
|   providence|   true | String|省份|
|   status|  true |    Number|状态|
|   district|    true |  String|区域|
|   location|      | GeoPoint |位置坐标，[iOS](https://leancloud.cn/docs/leanstorage_guide-objc.html#地理位置), [Android](https://leancloud.cn/docs/leanstorage_guide-android.html#地理位置)|

以下为样例地址

```JSON
{
  "street1": "国定东路200号307室",
  "ACL": {
    "*": {
      "write": false,
      "read": false
    }
  },
  "city": "上海",
  "recipient": "蔡慷",
  "providence": "上海",
  "status": 0,
  "district": "杨浦",
  "objectId": "58b520d81b69e600587ad9d4",
  "createdAt": "2017-02-28T07:03:52.625Z",
  "updatedAt": "2017-02-28T07:22:40.863Z"
}
```