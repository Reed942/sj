#### 用户登入
##### post [/api/user/login](http://192.168.1.188:8080/EDServer/api/user/login "登入")

接收 post 参数

- user -string 邮箱 **必填**
- password -string 密码[加密]  **必填**

返回值示例

```json
{
    "code":"200",
    "description":"success",
    "detail":{
        "id":"5b1bdb5548d04070b1e417c058b6abca",
        "phone":"13188888888",
        "in_time":"2015-11-17 11:39:08",
        "token":"ff5109ecd8d946d9a10684036aab123e",
        "email":"sj@163.com",
        "nickname":"Reedmm",
        "age":21,
        "gender":true, -男:true ; 女:false
        "avatar":"http://hostname/upload/avatar/avatar.jpg",
        "signature":"生活就像一盒巧克力"
    }
}
```

-----

#### 设置用户信息
##### post [/api/user/setUserInfo](http://192.168.1.188:8080/EDServer/api/user/setUserInfo "设置用户信息")

接收 post 参数

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**
- age [年龄] -int 
- height [身高] -int
- weight [体重] -int
- plan [卡路里目标] -string

返回值示例

```json
{
    "code":"200",
    "description":"success",
    "detail":""
}
```

-----

#### 我的教练
##### post [/api/user/getMyCoach](http://192.168.1.188:8080/EDServer/api/user/getMyCoach "我的教练")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{
    "detail":{
        "coachname":"Johhny",
        "age":27,
        "descrip":"著名教练，时尚先生，健身达人，肌肉匀称",
        "sc":4,
        "gender":true,
        "avatar":null,
        "coachid":"3",
        "intime":"2015-12-03",
        "validtime":"2015-12-07 18:53:13",
        "country":"中国上海"
    },
    "description":"success",
    "code":"200"
}
```

------------

#### 最新5条教练评价
##### post [/api/fit/getLatestReply](http://192.168.1.188:8080/EDServer/api/fit/getLatestReply "评价")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{
    "detail":[
        {
            "content":"不错",
            "id":12,
            "completecount":20,
            "wrongcount":0,
            "title":"举哑铃",
            "time":"2015-12-15 11:26:17",
            "trainid":"c6490a62abfb4300a319ef43c418f8df",
            "coachname":"郑多燕",
            "traintime":"2015-12-15 07:09:38",
            "calorie":"4"
        },
        .
        .
        .
    ],
    "description":"success",
    "code":"200"
}
```

------------

#### 教练评价
##### post [/api/fit/getReplyByToUser](http://192.168.1.188:8080/EDServer/api/fit/getReplyByToUser "评价")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{
    "detail":[{
        "content":"不错",
        "id":12,
        "completecount":20,
        "wrongcount":0,
        "title":"举哑铃",
        "time":"2015-12-15 11:26:17",
        "trainid":"c6490a62abfb4300a319ef43c418f8df",
        "coachname":"郑多燕",
        "traintime":"2015-12-15 07:09:38",
        "calorie":"4"
    },
    .
    .
    .
    ]
    "description":"success",
    "code":"200"
}
```

------------

#### 历史锻炼记录(分页获取)
##### post [/api/fit/getHistoryTraining](http://192.168.1.188:8080/EDServer/api/fit/getHistoryTraining "历史锻炼")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**
- index [页码，默认第1页] -int

返回值示例

```json
{
    "detail":{
        "lastPage":false,
        "pageSize":10,
        "pageNumber":1,
        "list":[
            {
                "logo":"video2",
                "wrongcount":0,
                "trainid":"e5ed489bd80e425e837b3e83acb37c7a",
                "completecount":0,
                "recordtime":"2015-12-23 17:02:27",
                "courseid":35,
                "calorie":"0",
                "coursename":"举哑铃"
            },
            .
            .
            .
        ]
    }
}

```

------------

#### 今日锻炼记录
##### post [/api/fit/todayTraining](http://192.168.1.188:8080/EDServer/api/fit/todayTraining "今日已锻炼")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{"detail":[{
    "wrongcount":97,
    "trainid":"6fcb9ce3bf5043d19d883a32a6272ded",
    "courseid":35,
    "completecount":97,
    "courselogo":"logo.png",
    "recordtime":"2015-12-23 13:29:20",
    "calorie":"0",
    "coursename":"举哑铃"
    },
    .
    .
    .
    ],
    "description":"success",
    "code":"200"
}
```

------------

#### 获取锻炼记录动作细分
##### post [/api/fit/getDetailPushCode](http://192.168.1.188:8080/EDServer/api/fit/getDetailPushCode "动作细分")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**
- _id [锻炼记录返回的 trainid] -string **必填**

返回值示例

```json
{
    "code":"200",
    "description":"success",
    "detail":[
        {
           "matchStatus":1,
           "type":2,
           "name":"\u5DE6\u62AC\u624B",
           "part":1,
           "time":53.0073013305664,
           "group":6,
           "cmpPer":0.933333337306976,
           "direction":"\u5DE6\u624B\u81C2\u4FDD\u6301\u5411\u4E0B\u5F2F\u66F2"
        },
        .
        .
        .
    ]
}
```

------------

#### 今日课程计划
##### post [/api/fit/todayCoursePlan](http://192.168.1.188:8080/EDServer/api/fit/todayCoursePlan "今日计划")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{"detail":[{
    "pushtime":"2015-12-23 11:20:29",
    "id":145,
    "courselogo":"video3",
    "courseid":6,
    "trainid":'2df3bf026a8145d9a8a969f97140d9e9',
    "coursename":"推肩（偏前束）",
    "unfinished":true -是否未锻炼
    },
    .
    .
    .
    ],
    "description":"success",
    "code":"200"
}
```

------------

#### 历史课程计划(包含今天)
##### post [/api/fit/getHistoryCoursePush](http://192.168.1.188:8080/EDServer/api/fit/getHistoryCoursePush "历史计划")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**
- count [历史天数,默认2天] -int 

返回值示例

```json
{"detail":[{
    "pushtime":"2015-12-23 11:20:29",
    "id":145,
    "courselogo":"video3",
    "courseid":6,
    "trainid":'2df3bf026a8145d9a8a969f97140d9e9',
    "coursename":"推肩（偏前束）",
    "unfinished":true -是否未锻炼
    },
    .
    .
    .
    ],
    "description":"success",
    "code":"200"
}
```

------------

#### 今日卡路里总和
##### post [/api/fit/todayCalorieSum](http://192.168.1.188:8080/EDServer/api/fit/todayCalorieSum "今日卡路里总和")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{"detail":
    {
        "caloriesum":100.0
    },
    "description":"success",
    "code":"200"
}
```

------------

#### 今日最佳纪录
##### post [/api/fit/todayMaxTraining](http://192.168.1.188:8080/EDServer/api/fit/todayMaxTraining "今日最佳纪录")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json

```

------------

#### 历史健身总计(时间从昨天开始一次往前)
##### post [/api/fit/historyTotal](http://192.168.1.188:8080/EDServer/api/fit/historyTotal "历史健身总计")

接收 post 参数 

- token [登入成功返回的用户标识]  -string  **必填**
- uid  [登入成功返回的用户标识]  -string  **必填**

返回值示例

```json
{"detail":[{
    "motionsum":100,
    "caloriesum":10.0
    },
    {
    "motionsum":100,
    "caloriesum":50.0
    },
    .
    .
    .
    "description":"success",
    "code":"200"
}
```

------------


