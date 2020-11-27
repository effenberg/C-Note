# C-Note
study on C#

---

# Chapter3 Objects & Types #

** out in Parameters **

out关键字通过引用传递参数。 它与 ref 关键字相似，只不过 ref 要求在传递之前初始化变量。 若要使用 out 参数，方法定义和调用方法均必须显式使用 out 关键字。作为 out 参数传递的变量在方法调用中传递之前不必进行初始化。 但是，被调用的方法需要在返回之前赋一个值。

```
 // version 2
            string input2 = Console.ReadLine();
            if (int.TryParse(input2, out int result2))
            {
                Console.WriteLine($"result: {result2}");
            }
            else
            {
                Console.WriteLine("not a number");
            }
```            

in modifier guarantees that the data this is sent into the method does not change (when passing a value type)

**Nullable Types**
```
int? x3= null;

int x5 = x3.HasValue ? x3.Value : -1;

int x6 = x3 ?? -1;
```
**Enum Types**
```
[Flags] //Attributes
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
# Chapter 4 Object Oriented Programming #

**Virtual**
1. method signature: all parameter type and the method name
2. Neither member fild nor static functions can be declard as virtual. Only for declaring method and property.
3. In C#, functuions are not virtual bydefault, but can be explicitly declared as virtual. By contrast, all functions in Java are virtual.

**Hiding Methods**

The new method modifier is to deal with version conflicts and react to changes on base classes after the derived class was done.

**Calling Base Versions of Methods**

base.<MethodName>

**Abstract Classes Methods**

1. An abstract class cannot be instantiated， whereas an abstract method does not have an implementation and must be overridden in any nonabstract derived class. If any class contains any abstract methods, that class must be declared as an abstract.
2. The sealed modifier does not allow to create a subclass or override a method.




```

```




