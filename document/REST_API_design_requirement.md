# 一、协议
API与用户的通信协议，通常使用HTTPS协议。
# 二、域名
将API部署在专用域名下：
https://api.qrdining.com
# 三、版本
将API的版本号放入URL。
# 四、路径
在RESTful架构中，每个网址代表一种资源（resource），所以网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表格名对应。一般来说，数据库中的表都是同种记录的"集合"（collection），所以API中的名词也应该使用复数。
eg.
- https://api.qrdining.com/v1/menus
- https://api.qrdining.com/v1/dishes
- https://api.qrdining.com/v1/orders
# 五、HTTP动词
常用的HTTP动词有下面五个：
- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。
还有两个不常用的HTTP动词。
- HEAD：获取资源的元数据。
- OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。
examples:
- GET /dishes：列出所有菜品
- POST /dishes：新建一个菜品
- GET /dishes/ID：获取某个指定菜品的信息
- PUT /dishes/ID：更新某个指定菜品的信息（提供该菜品的全部信息）
- PATCH /dishes/ID：更新某个指定动物园的信息（提供该菜品的部分信息）
- DELETE /dishes/ID：删除某个菜品
# 六、过滤信息
如果记录数量很多，服务器不可能都将它们返回给用户。API应该提供参数，过滤返回结果。
- ?limit=10：指定返回记录的数量
- ?offset=10：指定返回记录的开始位置。
- ?page=2&per_page=100：指定第几页，以及每页的记录数。
- ?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
- ?animal_type_id=1：指定筛选条件
# 七、状态码
服务器向用户返回的状态码和提示信息，常见的有：

1.200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）。

2.201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功。

3.202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）。

4.204 NO CONTENT - [DELETE]：用户删除数据成功。

5.400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。

6.401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）。

7.403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的。

8.404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。

9.406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）。

10.410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的。

11.422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误。

12.500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功。
# 八、错误处理
如果状态码是4xx，就应该向用户返回出错信息。一般来说，返回的信息中将error作为键名，出错信息作为键值即可。
#九、返回结果
针对不同操作，服务器向用户返回的结果应该符合以下规范。
- GET /collection：返回资源对象的列表（数组）
- GET /collection/resource：返回单个资源对象
- POST /collection：返回新生成的资源对象
- PUT /collection/resource：返回完整的资源对象
- PATCH /collection/resource：返回完整的资源对象
- DELETE /collection/resource：返回一个空文档

以上文档参考：[RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)