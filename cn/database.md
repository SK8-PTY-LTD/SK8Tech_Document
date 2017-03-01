旅淘淘新版数据库以及后台使用了[LeanCloud](https://leancloud.cn)作为后端解决方案，本文档详细介绍了数据类型，以及使用方法。

# 数据类型

数据库包括了以下“类”

  1. [Address](#address)
  1. [Comment](#comment)
  1. [Moment](#moment)
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
| street1 | true |String| 详细地址第一行|
| street2 | |String| 详细地址第二行 |
| city | true | String| 城市|
| recipient| true | String|收件人|
| contactNumber | true | String |手机号|
| providence| true | String|省份|
| status| true | Number|状态|
| district| true | String|区域|
| location| | GeoPoint |位置坐标，[iOS](https://leancloud.cn/docs/leanstorage_guide-objc.html#地理位置), [Android](https://leancloud.cn/docs/leanstorage_guide-android.html#地理位置)|

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

## Comment 

Comment为用户发布的“评论”，其中包括对[“瞬间”](#moment), [“需求”](#quest), 和[“推荐”](#recommendation)的评论。键名解释如下:

| 键名 | 必填 |类型| 注释 |
|------|------|------|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| type| true | Number| 评论类型，1为[“瞬间”](#moment)评论, 2为[“推荐”](#recommendation)评论, 3为[“需求”](#quest)评论|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| replyTo| | [_Comment](#comment) |回复状态|
| moment| |[_Moment](#moment)|[“瞬间”](#Moment)指针|
| recommendation| | [_Recommendation](#Recommendation)|[“推荐”](recommendation)指针
| quest| | [_Quest](#quest)|[“需求”](#Quest)指针|

以下为样例地址

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
  "*owner": "_User",
  "*content": "max_200_char",
  "*type": 1, //1: Moment, 2: Recommendation, 3, Quest
  "*status": 0, //Initialized: 0, Saved: 100, Reported: 400, Delisted: 800, Deleted: 900
  "replyTo": "_Comment",
  "moment": "_Moment",
  "recommendation": "_Recommendation",
  "quest": "_Quest",
}
```

## Moment

Moment 为用户发布的“瞬间”。键名解释如下：

| 键名 | 必填 |类型| 注释 |
|------|------|------|--|
| owner| true |[_User](#user)| 发布人|
| content| true |String| 评论内容，纯文字，最多200字 |
| imageArray| true |Array| 图片数组，至少一张图，最多九张图|
| viewNumber| true |Number| 总浏览数，默认值0,进入详情页面时+1|
| likeNumber| true |Number| 总点赞数，默认值0,详情页点赞时+1|
| commentNumber| true |Number|总评论数，默认值0,详情页评论时+1|
| status| true | Number|状态码，0=临时保存，100=已发布，400=已举报，800=官方下线，900=自主删除|
| pastView | true|Array|过去30天浏览量，过去一天就是第一个数字，默认[0,0...0]，30个0|
| pastViewTotal | true | Number| 过去30天浏览量总数，虽pastView更新|
| location| true | Number| 过去30天浏览量总数，虽pastView更新|

```JSON
 {
        "_id": "auto_id",
        "createdAt": "auto_date",
        "updatedAt": "auto_date",
        "ACL": "auto_ACL",
        "*owner": "_User",
        "*content": "max_200_char",
        "*imageArray": ["_File", "_File", "_File"],
        "*viewNumber": 0,
        "*likeNumber": 0,
        "*commentNumber": 0,
        "*status": 0, //Initialized: 0, Saved: 100, Reported: 400, Delisted: 800, Deleted: 900
        "*pastView": [0, 2, 30, 2, 3, 4, 6, 7, 8, 9, 10, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
        "location": {
            "fullname": "朝阳区",
            "country": "China",
            "location": {
                "lat": "39.921470",
                "lng": "116.443108"
            }
        }
    }
```