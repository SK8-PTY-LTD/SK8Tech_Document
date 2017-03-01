旅淘淘新版数据库以及后台使用了[LeanCloud](https://leancloud.cn)作为后端解决方案，本文档详细介绍了数据类型，以及使用方法。

# 使用方法

请结合本文档以及[LeanCloud REST API指南](https://leancloud.cn/docs/rest_api.html#API_版本)。

# 数据类型

数据库包括了以下“类”

  1. [Address](#address)
  1. [Comment](#comment)
  1. [Moment](#moment)
  1. [Recommendation](#recommendation)
  1. [Quest](#quest)
  1. [Order](#order)
  1. [Product](#product)
  1. [Transaction](#transaction) 
  1. [_User](#user)
  
## Address

Address为用户保存的“收货地址”，键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| street1 | true |String| 详细地址第一行|
| street2 | |String| 详细地址第二行 |
| city | true | String| 城市|
| recipient| true | String|收件人|
| contactNumber | true | String |手机号|
| providence| true | String|省份|
| status| true | Number|状态|
| district| true | String|区域|
| owner| true | [_User](#user)|地址的拥有人|
| location| | GeoPoint |位置坐标，[iOS](https://leancloud.cn/docs/leanstorage_guide-objc.html#地理位置), [Android](https://leancloud.cn/docs/leanstorage_guide-android.html#地理位置)|

以下为数据样例



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
"owner": "_User",
"objectId": "58b520d81b69e600587ad9d4",
"createdAt": "2017-02-28T07:03:52.625Z",
"updatedAt": "2017-02-28T07:22:40.863Z"
}
```

## Comment 

Comment为用户发布的“评论”，其中包括对[“瞬间”](#moment), [“需求”](#quest), 和[“推荐”](#recommendation)的评论。键名解释如下:

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| type| true | Number| 评论类型，1为[“瞬间”](#moment)评论, 2为[“推荐”](#recommendation)评论, 3为[“需求”](#quest)评论|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| replyTo| | [_Comment](#comment) |回复状态|
| moment| |[_Moment](#moment)|[“瞬间”](#Moment)指针|
| recommendation| | [_Recommendation](#Recommendation)|[“推荐”](recommendation)指针
| quest| | [_Quest](#quest)|[“需求”](#Quest)指针|

以下为数据样例



```JSON
{
  "objectId": "58b520d81b69e600587ad9d4",
  "createdAt": "2017-02-28T07:03:52.625Z",
  "updatedAt": "2017-02-28T07:22:40.863Z"，
  "ACL": {
    "*": {
      "write": false,
      "read": false
    }
  },
  "owner": "_User",
  "content": "max_200_char",
  "type": 1,
  "status": 0,
  "replyTo": "_Comment",
  "moment": "_Moment",
  "recommendation": "_Recommendation",
  "quest": "_Quest",
}
```

## Moment

Moment 为用户发布的“瞬间”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| imageArray| true |Array| 图片数组，至少一张图，最多九张图|
| viewNumber| true |Number| 总浏览数，默认值0,进入详情页面时+1|
| likeNumber| true |Number| 总点赞数，默认值0,详情页点赞时+1|
| commentNumber| true |Number|总评论数，默认值0,详情页评论时+1|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| pastView | true|Array|过去30天浏览量，过去一天就是第一个数字，默认[0,0...0]，30个0|
| pastViewTotal | true | Number| 过去30天浏览量总数，虽pastView更新|
| location| true |Object| 瞬间发布时候的地理位置json，见百度地图[Place详情检索服务](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-placeapi)|


以下为数据样例



```JSON
 {
        "_id": "auto_id",
        "createdAt": "auto_date",
        "updatedAt": "auto_date",
        "ACL": "auto_ACL",
        "owner": "_User",
        "content": "max_200_char",
        "imageArray": ["_File", "_File", "_File"],
        "viewNumber": 0,
        "likeNumber": 0,
        "commentNumber": 0,
        "status": 0,
        "pastView": [0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0],
    "pastViewTotal": 28,
        "location": {
            "fullname": "朝阳区",
            "country": "China",
            "location": {
              "name": "百度大厦员工食堂",
              "location": {
                "lng": 116.308022,
                "lat": 40.056892
              },
              "address": "海淀区上地十街10号(近辉煌国际)"
            }
        }
    }
```

## Recommendation

Recommendation 为用户发布的“推荐”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| imageArray| true |Array| 图片数组，至少一张图，最多九张图|
| viewNumber| true |Number| 总浏览数，默认值0,进入详情页面时+1|
| likeNumber| true |Number| 总点赞数，默认值0,详情页点赞时+1|
| commentNumber| true |Number|总评论数，默认值0,详情页评论时+1|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| pastView | true|Array|过去30天浏览量，过去一天就是第一个数字，默认[0,0...0]，30个0|
| pastViewTotal | true | Number| 过去30天浏览量总数，虽pastView更新|
| purchase| true | Boolean | 该推荐买手是否能够代购，详细描述[请见任务](https://www.teambition.com/project/587f23e78ea93ee9012bb448/tasks/scrum/587f23e7b9724a7664692c10/task/589d3bb43f59cac118855850) | 
| location| true |Object| 瞬间发布时候的地理位置json，见百度地图[Place详情检索服务](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-placeapi)|


以下为数据样例



```JSON
{
"_id": "auto_id",
"createdAt": "auto_date",
"updatedAt": "auto_date",
"ACL": "auto_ACL",
"owner": "_User",
"content": "max_200_char",
"imageArray": ["_File", "_File", "_File"],
"viewNumber": 0,
"likeNumber": 0,
"commentNumber": 0,
"status": 0,
"pastView": [0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0],
"pastViewTotal": 28
"purchase": true,
"location": {
"fullname": "朝阳区",
"country": "China",
"location": {
"name": "百度大厦员工食堂",
"location": {
"lng": 116.308022,
"lat": 40.056892
},
"address": "海淀区上地十街10号(近辉煌国际)"
}
}
}
```
## Quest

Quest为用户发布的“需求”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| imageArray| true |Array| 图片数组，至少一张图，最多九张图|
| viewNumber| true |Number| 总浏览数，默认值0,进入详情页面时+1|
| likeNumber| true |Number| 总点赞数，默认值0,详情页点赞时+1|
| commentNumber| true |Number|总评论数，默认值0,详情页评论时+1|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| pastView | true|Array|过去30天浏览量，过去一天就是第一个数字，默认[0,0...0]，30个0|
| pastViewTotal | true | Number| 过去30天浏览量总数，虽pastView更新|
| location| true |Object| 瞬间发布时候的地理位置json，见百度地图[Place详情检索服务](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-placeapi)|


以下为数据样例


```JSON
{
  "_id": "auto_id",
  "createdAt": "auto_date",
  "updatedAt": "auto_date",
  "ACL": "auto_ACL",
  "owner": "_User",
  "content": "max_200_char",
  "imageArray": ["_File", "_File", "_File"],
  "viewNumber": 0,
  "likeNumber": 0,
  "commentNumber": 0,
  "status": 0,
  "pastView": [0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,   1, 1, 1, 1, 1, 0],
  "pastViewTotal": 28,
  "location": {
    "fullname": "朝阳区",
    "country": "China",
    "location": {
      "name": "百度大厦员工食堂",
      "location": {
        "lng": 116.308022,
        "lat": 40.056892
      },
      "address": "海淀区上地十街10号(近辉煌国际)"
    }
  }
}
```

## Order

Order 为卖家（买手）发布的“订单”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
| conversation| true |[_Conversation](https://leancloud.cn/docs/realtime_v2.html)| 该订单发起的订单|
| buyer| true |[_User](#user)| 订单的买家|
| seller| true |[_User](#user)| 订单的卖家|
| product|true|[_Product](#product)| 订单中的产品 |
|quantity|true|Number| 商品代购数量，默认0|
|totalPriceInCent|true|Number|  订单总价，已分为单位的**整数**，如12.35元，存为1235|
|status|true|Number|状态码，0=买手出价，100=买家支付，200=买手买到，300=已发货，400=交易完成（已确认收货），详情见图|
|note||String|订单备注，最多200字|
| location| true |Object| 瞬间发布时候的地理位置json，见百度地图[Place详情检索服务](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-placeapi)|


以下为数据样例


```JSON
{
        "_id": "auto_id",
        "createdAt": "auto_date",
        "updatedAt": "auto_date",
        "ACL": "auto_ACL",
        "conversation": "_Conversation",
        "buyer": "_User",
        "seller": "_User",
        "product": "_Product",
        "quantity": 0,
        "totalPriceInCent": 0,
        "status": 0,
        “note": "max_200_char",
        "location": {
          "fullname": "朝阳区",
          "country": "China",
          "location": {
            "name": "百度大厦员工食堂",
            "location": {
              "lng": 116.308022,
              "lat": 40.056892
            },
            "address": "海淀区上地十街10号(近辉煌国际)"
          }
        }
}
```

## Product

Product 为卖家（买手）发布的“订单”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
|owner|true|[_User](#user)|发布人（买手）|
|name|true|String|产品名字|
|type|true|String|产品尺寸|
|imageArray|true|Array|产品照片，第一张默认封面|
|note||String|产品描述，最多200字|

以下数据样例

```JSON
{
        "_id": "auto_id",
        "createdAt": "auto_date",
        "updatedAt": "auto_date",
        "ACL": "auto_ACL",
        "owner": "_User",
        "name": "UGG靴子",
        "type": "",
        "imageArray": ["_File", "_File", "_File"],
        "note": "max_200_char",
    }
```

## Transaction

Transaction罗列了平台上**所有**的交易记录，包括充值，退款，订单付款，等。

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
|paymentInfo||Object|付款凭证|
|payer|true|[_User](#user)|付款人|
|payee|true|[_User](#user)|收款人|
|order|true|[_Order](#order)|订单指针|

以下数据样例

```JSON
{
"_id": "auto_id",
"createdAt": "auto_date",
"updatedAt": "auto_date",
"ACL": "auto_ACL",
"paymentInfo": {},
"payer": "_User",
"payee": "_User",
"order": "_Order",
}
```


## User

User为旅淘淘的所有用户列表。请见文档：[iOS](https://leancloud.cn/docs/leanstorage_guide-objc.html), [Android](https://leancloud.cn/docs/leanstorage_guide-android.html)

| 键名 | 必填 |类型| 注释 |
|------|------|------|------|
|username|true|String|用户的登录名，现在为手机号|
|nickname||String|昵称，非必填|
|status|true|Number|状态，默认0|
|bannerImage|true|_File|文件指针|
|profileImage|true|_File|文件指针|
|password|true|String|密码|
|officialName||String|真名，若真名或身份证号码则用户未认证|
|idNumber||String|身份证号码，若真名或身份证号码则用户未认证|
|dailyReward|true|Number|当天已获得的积分（盘缠），默认0|
|accumulatedReward|true|Number|用户已获得的总积分（盘缠），默认0|

以下数据样例

```JSON
 {
        "_id": "auto_id",
        "createdAt": "auto_date",
        "updatedAt": "auto_date",
        "ACL": "auto_ACL",
        "username": "1300xxxxxx",
        "nickname": "",
        "status": "",
        "bannerImage": "_File",
        "profileImage": "_File",
        "password": "xxx",
        "officialName": "",
        "mobileNumber": "1300xxxxxx",
        "idNumber": "310109xxxxxxxxxxxx", //身份照号码，买手认证
        "dailyReward": 0,
        "accumulatedReward": 0,
    }
```