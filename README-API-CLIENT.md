## Api for client flow

### Description of result and resultCode


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

 
### 3. orders service

#### 3.1 query for user
    
###### path:    /rental/orders/query
###### method:  post
###### param:
    param       | type   |  notNull     | desc          | example
    userId      | String |  notNull     | user id       | "100", Mike-100, Bos-001
###### result(data):
    param           | type   |  notNull  | desc             
    rows            | int    |  notNull  | brandList size   
    orderList       | list   |  notNull  | 
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
 
 
### 4. orders rent

#### 4.1 apply
###### path:    /rental/order/rent/apply
###### method:  post
###### param:
    param       | type   |  notNull     | desc              | example
    userId      | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo     | String |  notNull     | created by front  | "234567"
    brandId     | String |  notNull     | brandId of car    | "1"
    stockId     | String |  notNull     | stockId of car    | "1"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "SUBMIT_TIME"
    orderRentPriceEntity    | Object  |  nullable       | rental price      | 
    msg                 | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### result - all value for nextStep :
    value       |   desc
    SUBMIT_TIME |   step for submit rent time and repay time (format: yyyyMMdd hh:mm)
    PAY_PRICE   |   step for pay rental price
    TAKE_CAR    |   step for confirm to take car
###### param ex:
    {"userId":"100", "applyNo":"234567", "brandId":1, "stockId":1}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "SUBMIT_TIME",
            "msg": null,
            "orderRentPriceEntity": null,
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 4.2 submit time
###### path:    /rental/order/rent/time
###### method:  post
###### param:
    param               | type   |  notNull     | desc              | example
    userId              | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo             | String |  notNull     | created by front  | "234567"
    rentStartTime       | String |  notNull     | start time        | "20200105 12:00"
    rentEndTime         | String |  notNull     | end time          | "20200107 12:00"
    orderDiscountInfo   | Object |  nullable    | for discount      | [pending]
    days                | int    |  notNull     | rental days       | 2
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "SUBMIT_TIME"
    orderRentPriceEntity    | Object  |  nullable       | rental price      | 
    msg                     | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567", "rentStartTime":"20200105 12:00", "rentEndTime":"20200107 12:00", "days":2}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "PAY_PRICE",
            "msg": null,
            "orderRentPriceEntity": {
                "rentPrice": 60000,
                "discountPrice": 0,
                "guaranteeCharge": 100000,
                "serviceCharge": 10000
            },
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 4.3 pay
###### path:    /rental/order/rent/pay
###### method:  post
###### param:
    param           | type   |  notNull     | desc              | example
    userId          | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo         | String |  notNull     | created by front  | "234567"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "SUBMIT_TIME"
    orderRentPriceEntity    | Object  |  nullable       | rental price      | 
    msg                     | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "TAKE_CAR",
            "msg": null,
            "orderRentPriceEntity": null,
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 4.4 take car
###### path:    /rental/order/rent/take
###### method:  post
###### param:
    param           | type   |  notNull     | desc              | example
    userId          | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo         | String |  notNull     | created by front  | "234567"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "SUBMIT_TIME"
    orderRentPriceEntity    | Object  |  nullable       | rental price      | 
    msg                     | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": null,
            "msg": "恭喜用户喜提豪车，预祝您旅途愉快",
            "orderRentPriceEntity": null,
            "success": true,
            "finish": true
        },
        "map": null,
        "errorMsg": null
    }

#### 4.5 cancel apply
###### path:    /rental/order/rent/cancel
###### method:  post
###### param:
###### result(data):
###### param ex:
###### resule ex:


### 5. orders repay

#### 5.1 apply
###### path:    /rental/order/repay/apply
###### method:  post
###### param:
    param       | type   |  notNull     | desc              | example
    userId      | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo     | String |  notNull     | created by front  | "234567"
    stockId     | String |  notNull     | stockId of car    | "1"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "CHECK_CAR"
    orderRepayPriceEntity   | Object  |  nullable       | repay price       | 
    msg                 | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### result - all value for nextStep :
    value           |   desc
    CHECK_CAR       |   
    SETTLEMENT      |   
    CONFIRM_REPAY   |   
###### param ex:
    {"userId":"100", "applyNo":"234567", "stockId":1}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "CHECK_CAR",
            "msg": null,
            "orderRepayPriceEntity": null,
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 5.2 check car  
###### path:    /rental/order/repay/check
###### method:  post
###### param:
    param               | type   |  notNull     | desc              | example
    userId              | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo             | String |  notNull     | created by front  | "234567"
    isBroken            | boolean|  notNull     | is broken         | true/false
    breakageCharge      | long   |  nullable    | fine cherge if  broken     | >=0
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "CHECK_CAR"
    orderRepayPriceEntity   | Object  |  nullable       | repay price       | 
    msg                 | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567", "isBroken":true, "breakageCharge":200000}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "SETTLEMENT",
            "msg": null,
            "orderRepayPriceEntity": {
                "lateCharge": 0,
                "breakageCharge": 200000
            },
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 5.3 settlement
###### path:    /rental/order/repay/settlement
###### method:  post
###### param:
    param           | type   |  notNull     | desc              | example
    userId          | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo         | String |  notNull     | created by front  | "234567"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "CHECK_CAR"
    orderRepayPriceEntity   | Object  |  nullable       | repay price       | 
    msg                 | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": "CONFIRM_REPAY",
            "msg": null,
            "orderRentPriceEntity": null,
            "success": true,
            "finish": false
        },
        "map": null,
        "errorMsg": null
    }

#### 5.4 confirm repay
###### path:    /rental/order/repay/confirm
###### method:  post
###### param:
    param           | type   |  notNull     | desc              | example
    userId          | String |  notNull     | user id           | "100", Mike-100, Bos-001
    applyNo         | String |  notNull     | created by front  | "234567"
###### result(data):
    param                   | type    |  notNull        | desc              | example
    success                 | boolean |  notNull        | step finish       | true
    finish                  | boolean |  notNull        | flow finish       | false
    nextStep                | String  |  nullable       | next step         | "CHECK_CAR"
    orderRepayPriceEntity   | Object  |  nullable       | repay price       | 
    msg                 | String  |  nullable       | show to user if not null      | "Warn: car is broken down"
###### param ex:
    {"userId":"100", "applyNo":"234567"}
###### resule ex:
    {
        "success": true,
        "resCode": "000000",
        "resMsg": "成功",
        "data": {
            "nextStep": null,
            "msg": null,
            "orderRentPriceEntity": null,
            "success": true,
            "finish": true
        },
        "map": null,
        "errorMsg": null
    }
