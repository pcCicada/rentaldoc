## Api for admin flow

### Description of result and resultCode


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
    --id        | int    |  notNull  | brand id
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
    

### 2. stock service

#### 2.1 query
    
###### path:    /rental/stock/query
###### method:  post
###### param:
    param  | type   |  notNull  | desc          | example
    brand  | String |  nullable | brand of car  |"Toyota"
    model  | String |  nullable | model of car  |"Camry"
    color  | String |  nullable | color of car  |"black"
###### result(data):
    param               | type   |  notNull  | desc             
    rows                | int    |  notNull  | brandList size   
    stockList           | list   |  notNull  | 
    --brand             | String |  notNull  | brand of car
    --model             | String |  notNull  | model of car
    --color             | String |  notNull  | color of car
    --plateNumber       | String |  notNull  | plateNumber of car
    --dailyRentPrice    | long   |  notNull  | daily rent price
###### param ex:
    {"brand":"Toyota", "color": "white"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "rows": 1,
            "stockList": [
                {
                    "brand": "Toyota",
                    "model": "Camry",
                    "color": "white",
                    "plateNumber": "ZA9832"
                    "dailyRentPrice": 30000
                }
            ]
        },
        "map": null,
        "errorMsg": null
    }
 
#### 2.2 add
    
###### path:    /rental/stock/add
###### method:  post
###### param:
    param           | type   |  notNull | desc                  | example
    brandId         | int    |  notNull | id of brand           | 1
    plateNumber     | String |  notNull | plateNumber of car    | "XD4356"
    color           | String |  notNull | color of car          | "black"
    status          | String |  notNull | status of car         | "1",已出租-0,待出租-1,维护中-9
    dailyRentPrice  | long   |  notNull | daily rent price      | 40000
###### result(data):
    param               | type   |  notNull  | desc             
    rows                | int    |  notNull  | success rows   
###### param ex:
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
 

