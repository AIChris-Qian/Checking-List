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


#### 01 获取列
    
    select * from table

#### 02 获取行
    
    limit x：获取前 x 行     limit x，y / limit y offset x：获取第 x 行后 y 行的数据      where

#### 03 插入一列固定值
    
    select *，"XXX" as label from table

#### 04 对结果进行排序
   
    order by / asc / desc

**2. [ 数据预处理 ]**    
------------------------------

#### 01 缺失值处理

   缺失值：`空格 / null / 空值`
    
    空格：where XXX != " "   
    null：where XXX is not null
    空值：where XXX != ""     
    
    coalesce(null,value)   填充缺失值null的情况      if(XXX = "",a,XXX)   缺失值为空值    

#### 02 重复值处理

    distinct / group by

#### 03 重命名

    as


**3. [ 数据运算 ]**    
------------------------------

#### 01 比较运算
   
    <> / != 不等于    between 介于      is null / is not null

#### 02 数学运算

    abs() 绝对值   ceil() 大于 x 的最小整数值    floor() 小于 x 的最大整数值   
    rand() 0-1范围内的随机数    round(,2) 保留两位小数    sign() 正为1，负为-1，0为0
    
#### 03 字符串运算
   
    replace(str,a,b) 将 str 中的 a 替换成b     concat(a,b) 合并 a 和 b       concat_ws("-",a,b) 合并 a - b
    left("XXX",10) 截取左边10个字符       right("XXX",8) 截取右边8个字符      substring("XXX",6,2) 从第6位开始截取，长度为2    

#### 03 字符串匹配
    
    like "张%"   保证第一个字符是张      like "%凯%"   保证中间字符是凯
    like "张_"   姓张，名字为两个字      not like "张%" 保证第一个字符不是张
    
#### 04 字符串匹配

    repeat(str,x) 返回字符串 str 重复 x 次
 
    
#### 04 聚合运算

    count() null和空值不计入，空格计入   sum()  avg()   max()    min()
    var_pop() 总体方差   var_samp() 样本方差
    std() 总体标准差    stddev_samp() 样本标准差

**4. [ 控制函数 ]**    
------------------------------

#### 01 if() 函数
    
    if(condition,a,b)


#### 02 case when 函数
    
    case 
         when 条件1 then 返回值1
         when 条件2 then 返回值2
         else 返回默认值
    end 

**5. [ 日期和时间函数 ]**    
------------------------------

#### 01 获取当前时刻的数据
