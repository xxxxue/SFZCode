

# 根据身份证前六位的编号,查找归属地



# C# 核心代码

```csharp
/// <summary>
/// 根据身份证前六位的编号,查找归属地
/// </summary>
/// <param name="searchCode"></param>
public static string GetAreas(string searchCode)
{

    var path = @"./DataFiles/身份证行政区划代码.txt";

    var dataList = File.ReadAllLines(path);

    var splitSign = '　';

    var level = -1;

    var resList = new List<string>();

    for (int i = dataList.Length - 1; i > 0; i--)
    {
        if (level == 0)
        {
            break;
        }

        var item = dataList[i];

        if (item.Substring(0, 6) == searchCode)
        {
            AddToList(item);
            level = item.Count((a) => a == splitSign);
            level--;
            continue;
        }
        if (item.Count((a) => a == splitSign) == level)
        {
            AddToList(item);
            level--;
            continue;
        }
    }

    void AddToList(string data)
    {
        // 移除数字和空格
        data = Regex.Replace(data, @"\d", "")
            .Trim()
            .Replace("[", "")
            .Replace("]", "");
        resList.Add(data);
    }

    // 反转集合
    resList.Reverse();

    // 集合转字符串
    return String.Join(" ", resList);
}
```



# 调用

```csharp
// 调用
var res = MyUtils.GetAreas("140621");

Console.WriteLine(res); 
// 输出结果:
// 山西省 朔州市 山阴县
```

