（一）用户点餐子系统数据库设计

(1)order_detail

<img src= "https://raw.githubusercontent.com/E-Order/Dashboard/master/document/graph/order_detail.png">


```
CREATE TABLE `order_detail` (
  `detail_id` varchar(32) NOT NULL,
  `order_id` varchar(32) NOT NULL,
  `product_quantity` int(11) NOT NULL,
  `product_id` varchar(32) NOT NULL,
  `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  PRIMARY KEY (`detail_id`),
  KEY `index_order_id` (`order_id`),
  KEY `index_product_id` (`product_id`),
  CONSTRAINT `order_id` FOREIGN KEY (`order_id`) REFERENCES `order_master` (`order_id`) ON DELETE NO ACTION ON UPDATE NO ACTION,
  CONSTRAINT `product_id` FOREIGN KEY (`product_id`) REFERENCES `product_info` (`product_id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4

```

(2）order_master

<img src= "https://raw.githubusercontent.com/E-Order/Dashboard/master/document/graph/order_master.png">

```
CREATE TABLE `order_master` (
  `order_id` varchar(32) NOT NULL,
  `desk_id` int(11) NOT NULL,
  `seller_id` varchar(32) NOT NULL,
  `buyer_openid` varchar(64) NOT NULL,
  `order_amount` decimal(8,2) NOT NULL,
  `order_status` tinyint(3) NOT NULL DEFAULT '0',
  `pay_status` tinyint(3) NOT NULL DEFAULT '0',
  `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  PRIMARY KEY (`order_id`),
  KEY `index_buyer_openid` (`buyer_openid`),
  KEY `index_seller` (`seller_id`),
  CONSTRAINT `order_seller_id` FOREIGN KEY (`seller_id`) REFERENCES `seller_info` (`seller_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4
```
(3)product_info

<img src= "https://raw.githubusercontent.com/E-Order/Dashboard/master/document/graph/product_info.png">

```
CREATE TABLE `product_info` (
  `product_id` varchar(32) NOT NULL,
  `product_name` varchar(64) NOT NULL,
  `product_price` decimal(8,2) NOT NULL,
  `product_description` varchar(64) DEFAULT NULL,
  `product_icon` varchar(512) DEFAULT NULL,
  `product_stock` int(11) NOT NULL DEFAULT '0',
  `product_status` tinyint(3) DEFAULT '0',
  `category_type` int(11) NOT NULL,
  `seller_id` varchar(32) NOT NULL,
  `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  PRIMARY KEY (`product_id`),
  KEY `category_type_idx` (`category_type`),
  KEY `seller_id_idx` (`seller_id`),
  CONSTRAINT `product_category_type` FOREIGN KEY (`category_type`) REFERENCES `product_category` (`category_type`) ON DELETE NO ACTION ON UPDATE NO ACTION,
  CONSTRAINT `product_seller_id` FOREIGN KEY (`seller_id`) REFERENCES `seller_info` (`seller_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4
```
(4)product_cate

<img src= "https://raw.githubusercontent.com/E-Order/Dashboard/master/document/graph/product_cate.png">

```
CREATE TABLE `product_category` (
  `category_id` int(11) NOT NULL AUTO_INCREMENT,
  `category_name` varchar(64) NOT NULL,
  `category_type` int(11) NOT NULL,
  `seller_id` varchar(32) NOT NULL,
  `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  PRIMARY KEY (`category_id`),
  UNIQUE KEY `category_type` (`category_type`,`seller_id`),
  KEY `index_seller_id` (`seller_id`),
  CONSTRAINT `category_seller_id` FOREIGN KEY (`seller_id`) REFERENCES `seller_info` (`seller_id`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4
```
