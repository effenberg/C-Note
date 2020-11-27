# C-Note
study on C#

---

# Chapter3 Objects & Types #
**Nullable Types**
```
int? x3= null;

int x5 = x3.HasValue ? x3.Value : -1;

int x6 = x3 ?? -1;
```
**Enum Types**
```
[Flags]
    public enum DaysOfWeek
    {
        Monday = 0x1,
        Tuesday = 0x2,
        Wednesday = 0x4,
        Thursday = 0x8,
        Friday = 0x10,
        Saturday = 0x20,
        Sunday = 0x40,
        Weekend = Saturday | Sunday,
        Workday = 0x1f,
        AllWeek = Workday | Weekend
    }
}
```

Parse string to a Enum types TryPaser<T>. Return all names of enum Enum.GetNames(). Returen all values of enum Enum.GetValues(typeof(Enum)) 

```    
    private static void UsingEnumClass()
        {
            Color red;
            if (Enum.TryParse<Color>("Red", out red))
            {
                Console.WriteLine($"successfully parsed {red}");
            }

            string redtext = Enum.GetName(typeof(Color), red);
            Console.WriteLine(redtext);

            foreach (var day in Enum.GetNames(typeof(Color)))
            {
                Console.WriteLine(day);
            }


            foreach (short val in Enum.GetValues(typeof(Color)))
            {
                Console.WriteLine(val);
            }

            foreach (var item in Enum.GetValues(typeof(Color)))
            {
                Console.WriteLine(item);
            }
        }
```
**partial class**

不要把部分类以为是定义了多个类，其实还是一个类，只是把这个类拆分了。 在程序运行的时候编译器会把这个类合并在一起的， 这样做的好处是，当你有一个类很大的时候你可以按实现功能拆分在不同的文件中，这样就方便阅读和修改了。

** Extension Methods **

must be a static method, use the 'this' keyword the first parameter.

```
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









