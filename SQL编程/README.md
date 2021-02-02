# SQL编程
  by Chen Qian
     
    select
    from
    where
    group by
    having
    order by 
    limit
    
  执行顺序：
    
    from / where / group by / having / select / order by / limit

**1. [ 数据的获取 ]**    
------------------------------


#### 1.1 获取列
    
    select * from table

#### 1.2 获取行
    
    limit x：获取前 x 行     limit x，y / limit y offset x：获取第 x 行后 y 行的数据      where

#### 1.3 插入一列固定值
    
    select *，"XXX" as label from table

#### 1.4 对结果进行排序
   
    order by / asc / desc

**2. [ 数据预处理 ]**    
------------------------------

#### 2.1 缺失值处理

   缺失值：`空格 / null / 空值`
    
    空格：where XXX != " "   
    null：where XXX is not null
    空值：where XXX != ""     
    
    coalesce(null,value)   填充缺失值null的情况      if(XXX = "",a,XXX)   缺失值为空值    

#### 2.2 重复值处理

    distinct / group by

#### 2.3 重命名

    as


**3. [ 数据运算 ]**    
------------------------------

#### 3.1 比较运算
   
    <> / != 不等于    between 介于      is null / is not null

#### 3.2 数学运算

    abs() 绝对值   ceil() 大于 x 的最小整数值    floor() 小于 x 的最大整数值   
    rand() 0-1范围内的随机数    round(,2) 保留两位小数    sign() 正为1，负为-1，0为0
    
#### 3.3 字符串运算
   
    replace(str,a,b) 将 str 中的 a 替换成b     concat(a,b) 合并 a 和 b       concat_ws("-",a,b) 合并 a - b
    left("XXX",10) 截取左边10个字符       right("XXX",8) 截取右边8个字符      substring("XXX",6,2) 从第6位开始截取，长度为2    

#### 3.4 字符串匹配
    
    like "张%"   保证第一个字符是张      like "%凯%"   保证中间字符是凯
    like "张_"   姓张，名字为两个字      not like "张%" 保证第一个字符不是张
    
#### 3.5 字符串匹配

    repeat(str,x) 返回字符串 str 重复 x 次
 
    
#### 3.6 聚合运算

    count() null和空值不计入，空格计入   sum()  avg()   max()    min()
    var_pop() 总体方差   var_samp() 样本方差
    std() 总体标准差    stddev_samp() 样本标准差

**4. [ 控制函数 ]**    
------------------------------

#### 4.1 if() 函数
    
    if(condition,a,b)


#### 4.2 case when 函数
    
    case 
         when 条件1 then 返回值1
         when 条件2 then 返回值2
         else 返回默认值
    end 

**5. [ 日期和时间函数 ]**    
------------------------------

#### 5.1 获取当前时刻的数据
     
   日期和时间：`now()`  
   
   日期：`curdate() = date(now()) / year(now) / month(now()) / day(now())`
   
   时间：`curtime() = time(now()) / hour(now) / mintues(now()) / second(now())`
   
   周数：`weekofyear(now()) / dayofweek(now())`
   
#### 5.2 日期和时间运算

    date_add(date,interval num unit)      date_sub(date,interval num unit)        datediff(end_date,start_date)


**6. [ 数据分组与数据透视表 ]**    
------------------------------

#### 6.1  对分组后的数据进行聚合运算

    select 聚合运算 from table group by XXX
    
#### 6.2  对聚合后的数据进行条件筛选
     
     having   group_concat()   group by XXX with rollup

#### 6.3  数据透视表
     
     行列互换
     
**7. [ 窗口函数 ]**    
------------------------------

#### 7.1  聚合函数 + over() 函数

    avg(XXX) over()
    
#### 7.2  partition by 子句
     
     avg(XXX) over(partition by XXX)

#### 7.3  order by 子句
     
     avg(XXX) over(partition by XXX order by XXX)
     
#### 7.4  序列函数
     
     ntile(X)   分成 x 组
     row_number()   123  rank()  113   dense_rank()  112
     lag(XXX,1)   向后移动一位     lead(XXX,1)    向前移动一位 
     
     
     
**8. [ 多表连接 ]**    
------------------------------

#### 8.1  表的横向连接

    left join / right join / inner join / outer join 
    
#### 8.2  表的纵向连接

    union：纵向连接删除重复值
    union all：纵向连接不进行任何处理
     
     
 **9. [ 子查询 ]**    
------------------------------

#### 9.1  子查询的分类

    select 子查询
    from 子查询
    where 子查询 
    with 建立临时表
     
