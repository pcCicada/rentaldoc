## Api for admin flow

### 1. brand manage

#### 1.1 query
    
###### path:    /rental/brand/query
###### method:  post
###### param:
    param  | type   |  notNull  | desc          | example
    brand  | String |  nullable | brand of car  |"Toyota"
    model  | String |  nullable | model of car  |"Camry"
###### result(data):
    param       | type   |  notNull  | desc             
    rows        | int    |  notNull  | brandList size   
    brandList   | list   |  notNull  | 
    --brand     | String |  notNull  | brand of car
    --model     | String |  notNull  | model of car
###### param ex:
    {"brand":"BMW"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "rows": 1,
            "brandList": [
                {
                    "brand": "BMW",
                    "model": "650"
                }
            ]
        },
        "map": null,
        "errorMsg": null
    }
    
#### 1.2 add
    
###### path:    /rental/admin/brand/add
###### method:  post
###### param:
    param  | type   |  notNull  | desc          | example
    brand  | String |  notNull  | brand of car  |"Toyota"
    model  | String |  notNull  | model of car  |"Levin"
###### result(data):
    param       | type   |  notNull  | desc             
    rows        | int    |  notNull  | brandList size   
    brandList   | list   |  notNull  | 
    --brand     | String |  notNull  | brand of car
    --model     | String |  notNull  | model of car
###### param ex:
    {"brand":"Toyota","model":"Levin"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "rows": 1,
        },
        "map": null,
        "errorMsg": null
    }
###### remark
    There is a simple mock repository in the backend-system, whick is week to check duplicate data. 
    Please check before submit.
