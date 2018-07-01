# 码上点（扫码点餐系统）

这是一个扫码点餐系统，旨在通过手机点餐的方式，达到方便商家和客户的双赢。

---

**用户分客户和商家：**

客户扫码，进入指定商家的微信点餐界面进行点餐操作。

商家则通过PC端登入，进行查看订单，修改菜单等操作。

**优势：**

商家：减少商家的人力资源成本，提高客户点餐效率。

客户：更自由方便的点餐环境，更丰富的菜品介绍。


# 使用

商家客户端： http://123.207.7.251 （可使用user001  123456 登陆）

用户点餐系统：微信小程序



# [](#TOC)目录

&nbsp;&nbsp; 

* 1、[About](https://github.com/E-Order/Dashboard/blob/master/document/About.md)（项目规划）
* 2、[Team profile](https://github.com/E-Order/Dashboard/blob/master/document/Team_profile.md)（团队组建）
* 3、[Investigation](https://github.com/E-Order/Dashboard/blob/master/document/Investigation.md)（项目前期调研）
* 4、[Vision](https://github.com/E-Order/Dashboard/blob/master/document/Vision.md)（项目愿景）
* 5、[Product Backlog](https://github.com/E-Order/Dashboard/blob/master/document/Product_Backlog.md)（产品特性）
* 6、Requirement specification（需求规格说明）
    - 6.1 [Usecase Diagram](https://github.com/E-Order/Dashboard/blob/master/document/graph/%E7%94%A8%E4%BE%8B%E5%9B%BE.png)（用例图）
    - 6.2 [Use Cases](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/Use%20Cases%EF%BC%88%E7%94%A8%E4%BE%8B%EF%BC%89.mds)（用例+活动图）
    - 6.3 [Domian Model](https://github.com/E-Order/Dashboard/blob/develop/document/graph/Eorder_domain_model.png)（领域模型）
    
    - 6.4 [State Model](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%8A%B6%E6%80%81%E5%9B%BE.png?raw=true)（状态模型）

    - 6.5 System Sequence Diagram（功能模型）
        - 6.5.1 [扫码15331210](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331210_%E6%89%AB%E7%A0%81.png?raw=true)
        - 6.5.2 [点餐15331236](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/order_ssd.png?raw=true)
        - 6.5.3 [管理购物车15331209](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331209_%E7%AE%A1%E7%90%86%E8%B4%AD%E7%89%A9%E8%BD%A6.png?raw=true)
        - 6.5.4 [提交订单15331236](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/post_order_ssd.png?raw=true)
        - 6.5.5 [处理付款15331213](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331213_%E5%A4%84%E7%90%86%E4%BB%98%E6%AC%BE.md)
        - 6.5.6 [添加商品15331217](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331217-%E6%B7%BB%E5%8A%A0%E5%95%86%E5%93%81.png?raw=true)
        - 6.5.7 [更新商品15331217](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331217-%E6%9B%B4%E6%96%B0%E5%95%86%E5%93%81.png?raw=true)
        - 6.5.8 [添加种类15331217](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331217-%E6%B7%BB%E5%8A%A0%E7%A7%8D%E7%B1%BB.png?raw=true)
        - 6.5.9 [删除商品15331198](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331198_%E5%88%A0%E9%99%A4%E5%95%86%E5%93%81.PNG?raw=true)
        - 6.5.10 [删除种类15331198](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/15331198_%E5%88%A0%E9%99%A4%E5%95%86%E5%93%81%E7%A7%8D%E7%B1%BB.PNG?raw=true)
        - 6.5.11 [查看订单15331286](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/%E7%B3%BB%E7%BB%9F%E9%A1%BA%E5%BA%8F%E5%9B%BE/%E6%9F%A5%E7%9C%8B%E8%AE%A2%E5%8D%95_15331286.png?raw=true)
    - 6.6 [Supplementary Requirements](https://github.com/E-Order/Dashboard/blob/master/document/Requirement_Specification/SupplementaryRequirements.md)
* 7、Design（设计）
    - 7.1 UI design
        - [点餐 用例 UI设计(小程序端UI设计)](https://github.com/E-Order/Dashboard/blob/master/document/Design/UI_design/UI%20Design.md)
    - 7.2 Database design
        - 7.2.1 [用户及权限系统数据库设计](https://github.com/E-Order/Dashboard/blob/develop/document/Design/Database_design/%E6%95%B0%E6%8D%AE%E5%BA%93%E8%AE%BE%E8%AE%A1.md)
        - 7.2.2 XX子系统数据库设计 
        - 7.2.x 第三方数据评审结果
    - 7.3 [API 设计](https://ordermeal.docs.apiary.io/#)
    - 7.4 [Software Architecture Document](https://github.com/E-Order/Dashboard/blob/master/document/Software%20Architecture%20Document.md)
    - 7.5 [Usecase design]
* 8、生产规范与指南
    - 8.1 XX 代码规范
    - 8.2 [REST API 设计规范](https://github.com/E-Order/Dashboard/blob/master/document/REST_API_design_requirement.md)
    - 8.3 [逻辑架构到应用程序映射指南]
    - 8.4 [物理架构云上部署 dock-compose.yml 文件编写与使用]

* X1 meet_recording
    - inception meeting (yy/mm/dd)
    - [点击此处查看会议记录](https://github.com/E-Order/Dashboard/blob/master/document/meet_recording.md)
* X2 Tech/Work Report
    - 15331209-Deele：[Eclipse使用（Java基础）&Spring boot学习（一） ](https://blog.csdn.net/qq_32335095/article/details/79889667)
    - 15331213-Evene：[MySQL的下载安装及使用](https://blog.csdn.net/qq_35278061/article/details/79890250)
    - 15331217-south270：[初识SpringBoot](https://south270.github.io/blog/2018/04/12/first-study-report/)
    - 15331210-Ulricalin：[github团队项目管理入门](https://blog.csdn.net/ulricalin/article/details/79948569)
    - 15331198-KatharinaLin：[微信小程序技术学习](https://blog.csdn.net/KatharinLin/article/details/79921398)
    - 15331236-NooraMa：[微信小程序项目结构](https://ltimmy.github.io/%E5%BE%AE%E4%BF%A1%E5%B0%8F%E7%A8%8B%E5%BA%8F%E5%BC%80%E5%8F%91%E5%AD%A6%E4%B9%A0%E6%8A%A5%E5%91%8A/)
    - 15331286-Valerie：[微信小程序(1)](https://blog.csdn.net/joker_yy/article/details/79947404)

* X3 [Final Report](https://github.com/E-Order/Dashboard/tree/master/document/final_report)
* XX 建模练习
    - [Problem](https://github.com/E-Order/modelling_practice/blob/master/%E6%90%BA%E7%A8%8B%E7%81%AB%E8%BD%A6%E7%A5%A8%E9%A2%84%E8%AE%A2%E6%96%87%E6%A1%A3.md)
    - [Answer](https://github.com/E-Order/modelling_practice/tree/master/answer)
* XX 项目gif
    - [项目gif](https://github.com/E-Order/Dashboard/blob/master/document/ls6i4-ae9kw.gif)
