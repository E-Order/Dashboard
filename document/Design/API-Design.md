
# Order Meal API
Our Design of API. 


##  买家端用户 [/eorder/login/]
### 微信授权登录 [GET /eorder/login/start/]

+ Request (application/json)

        {
            "code": "---"
        }
        
+ Response 200 (application/json)

        {
            "session_key": "---",
            "openid":" ---"
        }

##  买家端商品 [/eorder/buyer/product/]
### 查询商品列表 [GET /eorder/buyer/product/list]

+ Request (application/json)

        {
            "sellerId": "12232"
        }

+ Response 200 (application/json)
   
        {
        "code": 0,
        "msg": "成功",
        "data": [
                    {
                        "name": "热榜",
                        "type": 1,
                        "foods": [
                                    {
                                        "id": "11",
                                        "name": "麦辣鸡翅2块",
                                        "price": 11.5,
                                        "description": "2块麦辣鸡翅 主要原料: 鸡肉，腌料，裹粉，油",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/hot3.jpg"
                                    },
                                    {
                                        "id": "12",
                                        "name": "麦乐鸡5块",
                                        "price": 11.5,
                                        "description": "5块麦乐鸡 主要原料: 鸡肉，油",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/hot2.jpg"
                                    },
                                    {
                                        "id": "13",
                                        "name": "原味板烧鸡腿堡配中薯套餐",
                                        "price": 32,
                                        "description": "1个原味板烧鸡腿堡+1份薯条(中)+1杯可口可乐(中)",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/hot1.jpg"
                                    },
                                    {
                                        "id": "14",
                                        "name": "奥利奥原味麦旋风",
                                        "price": 12.5,
                                        "description": "奥利奥原味麦旋风1个 主要原料：香草味冰淇淋，奥利奥饼干碎",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/hot4.png"
                                    }
                        ]
                    },
                    {
                        "name": "主食",
                        "type": 2,
                        "foods": [
                                    {
                                        "id": "21",
                                        "name": "经典麦辣鸡腿汉堡",
                                        "price": 20,
                                        "description": "1个经典麦辣鸡腿汉堡 主要原料：面包、鸡肉、生菜、风味酱",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/staple2.jpg"
                                    },
                                    {
                                        "id": "22",
                                        "name": "原味板烧鸡腿堡",
                                        "price": 20,
                                        "description": "1个原味板烧鸡腿堡 主要原料：面包、鸡肉、生菜、风味酱",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/staple4.jpg"
                                    },
                                    {
                                        "id": "23",
                                        "name": "巨无霸",
                                        "price": 23,
                                        "description": "1个巨无霸 主要原料：面包、牛肉、生菜、洋葱、腌黄瓜、芝士、风味酱",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/staple1.png"
                                    },
                                    {
                                        "id": "24",
                                        "name": "蜜汁鸡腿 满碗饭",
                                        "price": 24,
                                        "description": "1份蜜汁鸡腿满碗饭 主要原料：大米，鸡肉，生菜，油，风味酱",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/staple3.jpg"
                                    }
                        ]
                    },
                    {
                        "name": "小食",
                        "type": 3,
                        "foods": [
                                    {
                                        "id": "31",
                                        "name": "果木烟熏风味那么大鸡翅",
                                        "price": 16,
                                        "description": "那么大鸡翅-果木烟熏风味1个 主要原料：鸡肉，油",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack1.png"
                                    },
                                    {
                                        "id": "32",
                                        "name": "那么大鸡排",
                                        "price": 13,
                                        "description": "那么大鸡排1份 主要原料：鸡肉，油",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack2.png"
                                    },
                                    {
                                        "id": "33",
                                        "name": "香骨鸡腿",
                                        "price": 13,
                                        "description": "1个香骨鸡腿 主要原料：鸡肉，油",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack3.png"
                                    },
                                    {
                                        "id": "34",
                                        "name": "玉米杯",
                                        "price": 13,
                                        "description": "1个玉米杯 主要原料：玉米",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack4.png"
                                    }
                        ]
                    },
                    {
                        "name": "饮品",
                        "type": 4,
                        "foods": [
                                    {
                                        "id": "41",
                                        "name": "那么大珍珠奶茶",
                                        "price": 18,
                                        "description": "1杯那么大珍珠奶茶 主要原料：茶，焦糖珍珠",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/drink1.png"
                                    },
                                    {
                                        "id": "42",
                                        "name": "那么大鲜柠特饮(可乐)",
                                        "price": 13.5,
                                        "description": "1杯那么大鲜柠特饮(可口可乐) 主要原料：可口可乐，鲜柠檬片",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/drink2.png"
                                    },
                                    {
                                        "id": "43",
                                        "name": "那么大鲜柠特饮(雪碧)",
                                        "price": 13.5,
                                        "description": "1杯那么大鲜柠特饮(雪碧) 主要原料：雪碧，鲜柠檬片",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/drink3.png"
                                    },
                                    {
                                        "id": "44",
                                        "name": "鲜煮咖啡",
                                        "price": 11,
                                        "description": "1杯鲜煮咖啡 主要原料咖啡",
                                        "icon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/drink4.png"
                                    }
                        ]
                    }
                ]
        }

## 买家端订单 [/eorder/buyer/order]

### 创建订单 [POST /eorder/buyer/order/create]

+ Request (application/json)

        {
            "deskId": 10,
            "openid": "ew3euwhd7sjw9diwkq",
            "sellerId": "12232",
            "amount": 152.5,
            "items": [{
                "productId": "1423113435324",
                "productQuantity": 2
            }]
        }

+ Response 201 (application/json)


        {
            "code": 0,
            "msg": "成功",
            "data": {
            "orderId": "147283992738221" 
            }
        }

### 查询订单列表 [GET /eorder/buyer/order/list]

+ Request (application/json)

        {
            "openid": "ew3euwhd7sjw9diwkq",
            "sellerId": "1529320843657912713",
            "page": 0,
            "size": 10
        }
  
  
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功",
            "data": [
                {
                    "orderId": "161873371171128075",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128076",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                }
            ]
        }
        
### 查询订单详情 [GET /eorder/buyer/order/detail]

+ Request (application/json)

        {
            "openid": "18eu2jwk2kse3r42e2e",
            "sellerId": "12232",
            "orderId": "161899085773669363"
        }

+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功",
            "data": {
                "orderId": "161899085773669363",
                "deskId":"10",
                "buyerOpenid": "18eu2jwk2kse3r42e2e",
                "orderAmount": 18,
                "orderStatus": 0,
                "payStatus": 0,
                "createTime": 1490177352,
                "updateTime": 1490177352,
                "orderDetailList": [
                    {
                        "detailId": "161899085974995851",
                        "orderId": "161899085773669363",
                        "productId": "157875196362360019",
                        "productName": "招牌奶茶",
                        "productPrice": 9,
                        "productQuantity": 2,
                        "productIcon": "http://xxx.com"
                    },
                    {
                        "detailId": "161899085974995851",
                        "orderId": "161899085773669363",
                        "productId": "157875196362360020",
                        "productName": "麦辣鸡翅2块",
                        "productPrice": 11.5,
                        "productQuantity": 1,
                        "productIcon": "http://xxx.com"
                    }
                ]
            }
        }
        
### 取消订单 [POST /eorder/buyer/order/cancel]

+ Request (application/json)

        {
            "openid": 18eu2jwk2kse3r42e2e,
            "orderId": 161899085773669363
        }
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
  
### 支付订单 [POST /eorder/buyer/order/pay]

+ Request (application/json)

        {
            "openid": 18eu2jwk2kse3r42e2e,
            "orderId": 161899085773669363
        }
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
              
        }
        
## 卖家端用户 [/eorder/seller/signup]
### 用户注册 [POST /eorder/seller/signup]

+ Request (application/json)

        {
            "username": "klinjxx",
            "password": "123456",
            "telephone":"13215164987",
            "address":"Guangzhou"
        }


+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
        

### 用户登陆 [POST /eorder/seller/signin]

+ Request (application/json)

        {
            "username": "klinjxx",
            "password": "123456"
        }


+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
        
### 查询商家信息 [GET /eorder/seller/info]
+ Request (application/json)

        {}
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功",
            "data": {
                "username": "klinjxx",
                "password": "123456",
                "telephone":"13215164987",
                "address":"Guangzhou"
            }
        }

### 修改商家信息 [POST /eorder/seller/update]

+ Request (application/json)

        {
            "username": "klinjxx",
            "password": "123456",
            "telephone":"13215164987",
            "address":"Guangzhou"
        }

+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }

## 卖家端商品 [/eorder/seller/product]

### 查询商品列表 [GET /eorder/seller/product/list]

+ Request (application/json)

        {
            "page": 0, //从第0页开始
            "size": 10,
            "categoryType": 2
        }

+ Response 200 (application/json)
   
        {
            "code": 0,
            "msg": "成功",
            "total": 10,
            "data": [
                {
                    "productId": "123456",
                    "productName": "玉米杯",
                    "productPrice": 13,
                    "productDescription": "1个玉米杯 主要原料：玉米",
                    "productIcon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack4.png",
                    "productStock": 100,
                    "productStatus": 0,
                    "categoryType": 2,
                    "createTime": 1527320008000,
                    "updateTime": 1528564902000
                }, {
                    "productId": "44",
                    "productName": "鲜煮咖啡",
                    "productPrice": 11,
                    "productDescription": "1杯鲜煮咖啡 主要原料咖啡",
                    "productIcon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/drink4.png",
                    "productStock": 76,
                    "productStatus": 0,
                    "categoryType": 2,
                    "createTime": 1527324267000,
                    "updateTime": 1528893325000
                }
            ]
        }
        

### 商品上架 [POST /eorder/seller/product/onSale]

+ Request (application/json)

        {
            "productId": "123456"
        }

+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
        
        
### 商品下架 [POST /eorder/seller/product/offSale]

+ Request (application/json)

        {
            "productId": "123456"
        }
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
        
        
### 修改商品 [POST /eorder/seller/product/update]

+ Request (application/json)

        {
            "productId": "123456",
            "productName": "玉米杯",
            "productPrice": 13,
            "productDescription": "1个玉米杯 主要原料：玉米",
            "productIcon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack4.png",
            "productStock": 100,
            "productStatus": 0,
            "categoryType": 2,
        }

+ Response 201 (application/json)


        {
            "code": 0,
            "msg": "成功"
        }
        

### 添加商品 [POST /eorder/seller/product/add]

+ Request (application/json)

        {
            "productName": "玉米杯",
            "productPrice": 13,
            "productDescription": "1个玉米杯 主要原料：玉米",
            "productIcon": "https://raw.githubusercontent.com/LTimmy/markdownPhotos/master/snack4.png",
            "productStock": 100,
            "productStatus": 0,
            "categoryType": 2,
        }

+ Response 201 (application/json)


        {
            "code": 0,
            "msg": "成功",
            "data": {
            "productId": "1528962346721836038"
            }
        }
        
        
## 卖家端类目 [/eorder/seller/category]

### 查询商品类目 [GET /eorder/seller/category/list]

+ Request (application/json)

        {}

+ Response 200 (application/json)


        {
            "code": 0,
            "msg": "成功",
            "data": [
                {
                    "categoryId": 1,
                    "categoryName": "热销榜",
                    "categoryType": 2,
                    "createTime": 1527319989,
                    "updateTime": 1527319989
                },
                {
                    "categoryId": 2,
                    "categoryName": "女生专属",
                    "categoryType": 3,
                    "createTime": 1527319989,
                    "updateTime": 1527319989
                }
            ]
        }


### 修改商品类目 [POST /eorder/seller/category/update]
+ Request (application/json)

        {
            "categoryId": 12,
            "categoryName": "热销榜",
            "categoryType": 2
        }
+ Response 200 (application/json)


        {
            "code": 0,
            "msg": "成功"
        }

### 添加商品类目 [POST /eorder/seller/category/add]
+ Request (application/json)

        {
            "categoryName": "热销榜",
            "categoryType": 2
        }
+ Response 200 (application/json)


        {
            "code": 0,
            "msg": "成功",
            "data": [
                {
                    "categoryId": "123"
                }
            ]
        }

### 删除商品类目 [POST /eorder/seller/category/delete]
+ Request (application/json)

        {
            "categoryId": "12"
        }
+ Response 200 (application/json)


        {
            "code": 0,
            "msg": "成功"
        }
        
## 卖家端订单 [/eorder/seller/order]

### 查询订单列表 [GET /eorder/seller/order/list]

+ Request (application/json)

        {
            "orderId":,
            "deskId":,
            "orderStatus":,
            "payStatus":,
            "orderDate":"",
            "page": 0, 
            "size": 10
        }
  
  
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功",
            "total": 14,
            "data": {
                {
                    "orderId": "161873371171128075",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128076",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128077",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128078",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128079",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128080",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128081",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128082",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128083",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128084",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                },
                {
                    "orderId": "161873371171128085",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 152.1,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                    },
                    {
                        "orderId": "161873371171128086",
                        "deskId": 10,
                        "buyerOpenid": "18eu2jwk2kse3r42e2e",
                        "orderAmount": 64,
                        "orderStatus": 0,
                        "payStatus": 0,
                        "createTime": 1490171219,
                        "updateTime": 1490171219
                    },
                    {
                        "orderId": "161873371171128087",
                        "deskId": 10,
                        "buyerOpenid": "18eu2jwk2kse3r42e2e",
                        "orderAmount": 152.1,
                        "orderStatus": 0,
                        "payStatus": 0,
                        "createTime": 1490171219,
                        "updateTime": 1490171219
                    },
                {
                    "orderId": "161873371171128088",
                    "deskId": 10,
                    "buyerOpenid": "18eu2jwk2kse3r42e2e",
                    "orderAmount": 64,
                    "orderStatus": 0,
                    "payStatus": 0,
                    "createTime": 1490171219,
                    "updateTime": 1490171219
                }
            }
        }
        

### 查询订单详情 [GET /eorder/seller/order/detail]

+ Request (application/json)

        {
            "orderId": "161899085773669363"
        }

+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功",
            "data": {
                "orderId": "161899085773669363",
                "deskId":"10",
                "buyerOpenid": "18eu2jwk2kse3r42e2e",
                "orderAmount": 18,
                "orderStatus": 0,
                "payStatus": 0,
                "createTime": 1490177352,
                "updateTime": 1490177352,
                "orderDetailList": [
                    {
                        "detailId": "161899085974995851",
                        "orderId": "161899085773669363",
                        "productId": "157875196362360019",
                        "productName": "招牌奶茶",
                        "productPrice": 9,
                        "productQuantity": 2,
                        "productIcon": "http://xxx.com"
                    }
                ]
            }
        }
        
        
### 取消订单 [POST /eorder/seller/order/cancel]

+ Request (application/json)

        {
            "orderId": 161899085773669363
        }
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }
### 完结订单 [POST /eorder/seller/order/finish]
+ Request (application/json)
        {
            "orderId": 161899085773669363
        }
+ Response 200 (application/json)
        {
            "code":0,
            "msg":"成功"
        }

 


### 支付订单 [POST /eorder/seller/order/pay]

+ Request (application/json)

        {
            "orderId": 161899085773669363
        }
        
+ Response 200 (application/json)

        {
            "code": 0,
            "msg": "成功"
        }  

        
