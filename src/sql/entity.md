#  CourseEntity
-------------------------------------------------------
###  课程实体 courses
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|courses_id|INT UNSIGNED AUTO_INCREMENT|
|类型|c_type|TINYINT|音频：0，视频：1|
|标题|c_title|VARCHAR(30)|
|封面|c_cover|TEXT|
|作者|c_author_id|INT UNSIGNED|
|简介|c_intro|TEXT|
|时间|c_create_time|TIMESTAMP|
|价格|c_price|FLOAT|
|时长|c_duration|INTEGER|
|标签|c_label|SMALLINT|课程对应解决的问题类型|
|点赞数|c_likes|INT|
|备用1|c_bak1|TEXT|
|备用2|c_bak2|TEXT|


--------------------------------------------------------------

### 课程点赞记录course_likes
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|cl_id|INT UNSIGNED AUTO_INCREMENT|
|用户ID|cl_user_id|INT|
|课程ID|cl_course_id|INT|
|日期|cl_create_time|TIMESTAMP|

-----------------------------------------------------
###  用户 course_user
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|昵称|u_name|VARCHAR(10)|
|头像|u_avator|TEXT
|性别|u_sex|VARCHAR(4)|
|积分|u_integral|INT UNSIGNED|
|手机号|u_phone|VARCHAR(10)|
|单位|u_org|VARCHAR(50)|
|地址|u_address|VARCHAR(50)|
|备用1|u_bak1|TEXT|
|备用2|u_bak2|TEXT|

----------------------------------------------------------

###  类别 course_labels
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|标签名|l_name|VARCHAR(30)|

--------------------------------------------------------------

### 购买记录course_purchase
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|用户ID|p_user_id|INT|
|课程ID|p_course_id|INT|
|价格|p_price|FLOAT|
|日期|p_create_time|TIMESTAMP|

------------------------------------------------------------
### 积分交易记录course_integral_consume
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|用户ID|ic_user_id|INT|
|课程ID|ic_course_id|INT|
|价格|ic_price|FLOAT|
|日期|ic_create_time|TIMESTAMP|

------------------------------------------------------------
### 评论记录course_comment
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|用户ID|cc_user_id|INT|
|课程ID|cc_course_id|INT|
|评论ID|cc_comment_id|INT|如果为-1则为课程评论，否则为回复评论|
|评论内容|cc_comment_id|INT|
|日期|cc_create_time|TIMESTAMP|
|点赞数|cc_likes|INT|

--------------------------------------------------------------
### 评论点赞记录course_comment_likes
####  CHARSET=utf8
|属性|字段名|类型|备注|
|-|-|-|-|
|主键|id|INT UNSIGNED AUTO_INCREMENT|
|用户ID|ccl_user_id|INT|
|课程ID|ccl_course_id|INT|
|评论ID|ccl_comment_id|INT|
|日期|ccl_create_time|TIMESTAMP|


###  MYSQL 中文问题
#### /etc/mysql 找到my.cnf 追加
```
[mysqld]
collation-server = utf8_unicode_ci
init-connect='SET NAMES utf8'
character-set-server = utf8

[client]
default-character-set=utf8

[mysql]
default-character-set=utf8
```
