

# C#根据身份证前六位的编号,查找归属地



## 调用

```csharp
// 调用
var res = MyUtils.GetAreas("141124");

Console.WriteLine(res); 
// 输出结果:
// 山西省 吕梁市 临县
```



## 数据来源

> 如果github仓库中txt文件年份比较久, 
>
> 请自己从这个网站中复制粘贴到txt里

[最新县及县以上1980年以来历史行政区划代码大全](http://www.zxinc.org/gb2260.htm)

