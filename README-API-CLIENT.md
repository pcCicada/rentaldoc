## Api for client flow

### 1. brand service

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
    param           | type   |  notNull  | desc             
    rows            | int    |  notNull  | brandList size   
    stockList       | list   |  notNull  | 
    --brand         | String |  notNull  | brand of car
    --model         | String |  notNull  | model of car
    --color         | String |  notNull  | color of car
    --plateNumber   | String |  notNull  | plateNumber of car
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
                    "plateNumber": null
                }
            ]
        },
        "map": null,
        "errorMsg": null
    }
 



 
### 3. order service

#### 3.1 query for user
    
###### path:    /rental/order/query
###### method:  post
###### param:
    param  | type   |  notNull  | desc          | example
    brand  | String |  nullable | brand of car  |"Toyota"
    model  | String |  nullable | model of car  |"Camry"
    color  | String |  nullable | color of car  |"black"
###### result(data):
    param           | type   |  notNull  | desc             
    rows            | int    |  notNull  | brandList size   
    stockList       | list   |  notNull  | 
    --brand         | String |  notNull  | brand of car
    --model         | String |  notNull  | model of car
    --color         | String |  notNull  | color of car
    --plateNumber   | String |  notNull  | plateNumber of car
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
                    "plateNumber": null
                }
            ]
        },
        "map": null,
        "errorMsg": null
    }
 
 
