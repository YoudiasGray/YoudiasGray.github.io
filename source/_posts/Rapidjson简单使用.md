---
title: Rapidjson简单使用
date: 2019-07-15 21:39:12
tags:
  - rapidjson
---

# Rapidjson使用简介

## Rapidjson简介

官网：http://rapidjson.org/zh-cn/

一个高效的C++ JSon解析/生成器。

提供源码，只需要包含头文件即可，无依赖库问题。

性能据说最佳，虽说目前没遇到过解析json成为瓶颈的项目，快点总没错。

## 使用简介

rapidjson的使用很简单，只需要根据需要包含对应的头文件，然后进行解析即可。

### json格式



参考  https://www.json.cn/wiki.html

json基于两种结构：

1，对象，{}括起来的键值对，键值对之间用，隔开。值可以是任意的，可以是对象、数组、数字、字符串等

2，数组，用[]括起来的多个对象。

json的合法格式：

* 对象：无序的键值对集合，用{} 括起来，每个key后面一个：，key/value之间用,隔开

  值可以是双引号括起来的字符串、数值、true/false/null、对象或者数组

- 数组：对象列表

- 单独的字符串、数字、布尔值等也是合法的json格式。

  


参考http://www.json.org/

object：

![img](https://www.json.org/img/object.png)

array：

![img](https://www.json.org/img/array.png)

value:

![img](https://www.json.org/img/value.png)

所以以下测试中的字符串都是合法的json：

```c++
    test = "[{\"a\": 1},{\"a\": 2}]";
    TestJson(test);

    test = "123";
    TestJson(test);

    test = "abc";
    TestJson(test);

    test = "\"abc\"";
    TestJson(test);

    test = "{\"abc\":123}";
    TestJson(test);
```



## 解析

由于json格式各种各样，需要先进行判断才能进一步处理。

对json的使用很简单，首先包含头文件：

```
#include "..\..\..\XXX\rapidjson\rapidjson.h"
#include "..\..\..\XXX\rapidjson\document.h"
#include "..\..\..\XXX\rapidjson\stringbuffer.h"
#include "..\..\..\XXX\rapidjson\writer.h"
#include "..\..\..\XXX\rapidjson\prettywriter.h"
```

在代码中通过Document进行使用：

```
void TestJson(string str)
{
    Document doc;
    if (!doc.Parse(str.c_str()).HasParseError())
    {
        const Value& local = doc;
        if (local.IsArray())
        {
            cout << "is array" << endl;
            for (int i = 0; i < local.Size(); i++)
            {
                const Value& tmp = local[i];                
                cout << tmp["a"].GetInt() << endl;
            }
        }
        else if (local.IsObject())
        {
            cout << "is object" << endl;
        }
        else if (local.IsString())
        {
            cout << "is String" << endl;
            cout << local.GetString() << endl;
        }
        else if (local.IsBool())
        {
            cout << "is bool" << endl;
            cout << local.GetBool() << endl;
        }
        else if (local.IsInt())
        {
            cout << "is int" << endl;
            cout << local.GetInt() << endl;
        }        
    }
}
```

使用起来非常简单，如果是数组，遍历处理接口，如果是String，GetString就得到字符串值，如果是Int,GetInt,如果是嵌套类型，再次进行解析即可。



## 序列化

如果要构架json格式数据，也非常简单。

只需要rapidjson::StringBuffer和rapidjson::Writer\<rapidjson::string>配合即可，writer.StartObject()开始写入，依次指定key、value，完成后EndObject即可。

```c++
string TestGenerateJson()
{
    string result = "";
    rapidjson::StringBuffer strBuf;
    rapidjson::Writer<rapidjson::StringBuffer> writer(strBuf);
    
    writer.StartObject();
    writer.Key("abc");
    writer.String("cba");
    writer.EndObject();
    
    result = strBuf.GetString();
    return result;
}
```

其中默认构成的json字符串没有空格缩进等，可以通过prettyWriter生成更方便查看的json数据。

```c++
string TestGenerateJson()
{
    string result = "";
    rapidjson::StringBuffer strBuf; 
    rapidjson::PrettyWriter<rapidjson::StringBuffer> writer(strBuf);

    writer.StartObject();
    writer.Key("abc");
    writer.String("cba");
    writer.EndObject();
    
    result = strBuf.GetString();
    return result;
}
```

效果就是会自动缩进换行对齐，更方便阅读。