# C-Note
study on C#

**Nullable Types**
```
int? x3= null;

int x5 = x3.HasValue ? x3.Value : -1;

int x6 = x3 ?? -1;
```

**partial class**

不要把部分类以为是定义了多个类，其实还是一个类，只是把这个类拆分了。 在程序运行的时候编译器会把这个类合并在一起的， 这样做的好处是，当你有一个类很大的时候你可以按实现功能拆分在不同的文件中，这样就方便阅读和修改了。

** Extension Methods **
```
using ExtensionMethods.Foo;
using System;
// using ExtensionMethods.Bar; // importing both namespaces creates an ambiguous compiler error

    public static class StringExtensions
        {
            public static int GetWordCount(this string s) =>
                s.Split().Length;           
        }
    

    class Program
    {
        static void Main()
        {
            string fox = "the quick brown fox jumped over the lazy dogs down 9876543210 times";
            int wordCount = fox.GetWordCount();
            Console.WriteLine($"{wordCount} words");
            Console.ReadLine();
        }
    }
```







