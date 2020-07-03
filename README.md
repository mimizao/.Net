# 第一天

没什么特殊的，都是C++里面有的



# 第二天

## 注释

### ///

这里有了一个"///"的情况，一般放在类或者函数的上面，例子如下：

```c#
        /// <summary>
        /// 这个方法的作用是求两个整数之间的最大值
        /// </summary>
        /// <param name="n1">第一各整数</param>
        /// <param name="n2">第二个整数</param>
        /// <returns>返回比较大的那个数字</returns>
        public static int GetMax(int n1, int n2) {
            return n1 > n2 ? n1 : n2;
        }
```



## 快捷键

### region & endregion

隐藏冗余的代码块，"region"和"endregion"，如下：

```c#
            #region 这些代码实现了XX功能
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            Console.WriteLine("Hello World!");
            #endregion
```

不知道为啥效果显示不出来，但是在VS中是可以的，这里就是记录一下，不放图了。



## 变量

### decimal

一个原本没有接触过的数据类型，称为金钱类型，用来存储金钱，值后面需要加上一个m;

```c#
            decimal m = 231.33m;
```



### 变量命名规范

* Pascal：标识符中每个单词的首字母都大写，用于类型名和函数，如CarDeck，DealersHand

* Camel：除第一个单词以外，标识符中所有的单词的首字母都大写，用于本地变量和函数参数，如              totalCycleCount，randomSeedParam。

  

## +号的作用

* 连接：当+号两遍有一边是字符串的时候，+号就起到连接的作用。

* 相加：两边是数字的时候。

```c#
        static void Main(string[] args) {
            string name = "王五";
            Console.WriteLine("你好，" + name);//输出：你好，王五
            Console.ReadKey();

            Console.WriteLine(5 + 5);//输出：10
            Console.WriteLine(5 + "5");//输出：55
            Console.ReadKey();
        }
```



  ## 占位符

使用方法：先挖个坑，再填个坑

```c#
        static void Main(string[] args) {
            int n1 = 10;
            int n2 = 20;
            int n3 = 30;
            Console.WriteLine("第一个数字是{0},第二个数字是{1},第三个数字是{2}", n1, n2, n3);
            Console.ReadKey();
        }
```

注意事项：

* 你挖了几个坑，就填几个坑，如果你多填了，没效果。
* 你挖了几个坑，就填几个坑，如果你少填了，抛异常。  

输出顺序：按照挖坑的顺序来，例子如下：

```c#
        static void Main(string[] args) {
            int n1 = 10;
            int n2 = 20;
            int n3 = 30;
            Console.WriteLine("第一个数字是{0},第二个数字是{2},第三个数字是{1}", n1, n2, n3);
            Console.ReadKey();
        }
```

上面的输出结果是10，30，20。

再来一个例子：

```c#
        static void Main(string[] args) {
            int n1 = 10;
            int n2 = 20;
            int n3 = 30;
            Console.WriteLine("第一个数字是{1},第二个数字是{2},第三个数字是{0}", n1, n2, n3);
            Console.ReadKey();
        }
```

输出结果20，30，10。

来个练习：

```c#
            string name = "张三";
            char gender = '男';
            int age = 18;
            string tel = "12345678910";

            Console.WriteLine("我叫{0},我是{1}生，我今年{2}岁了，我的手机号是{3}", name, gender,age,tel);
            Console.ReadKey();
```



## 异常

异常是指：语法上并没有任何错误，只不过是程序在运行的期间，由于某些原因出现了问题，使程序不能再正常的运行。



## 接收用户的输入

```c#
        static void Main(string[] args) {
            Console.WriteLine("请输入你的姓名");
            string name = Console.ReadLine();
            Console.WriteLine("您的姓名是{0}", name);
        }
```



## 转义符

* \n：表示换行
* \“：表示一个英文半角的双引号
* \t：表示一个tab键的空格
* \b：表示一个退格键，放到字符串的两边没有效果
* \r\n：windows操作系统不认识\n，只认识\r\n
* \\\：表示一个\  



## @符号

* 取消\在字符串中的转义作用

* 将字符串按照原格式输出

```c#
            string path = "E:\全套精品.Net基础班视频教程-video\全套精品.Net基础视频教程之2-C#基础\（第二天）\video";
            string path = @"E:\全套精品.Net基础班视频教程-video\全套精品.Net基础视频教程之2-C#基础\（第二天）\video";
```

这里的两句代码，第一句就报错，因为并没有“\全套”等转义符，在最前面加上@就可以了。



```c#
            Console.WriteLine(@"孙
浩天");
```

这样就可以保留原格式输出了。



## 强制类型转换

```c#
            double n1 = 1.23;
            int n2 = (int)n1;
            Console.WriteLine(n2);
            Console.ReadKey();
```

输出1.



```c#
            int n1 = 10;
            int n2 = 3;
            double n3 = n1 / n2;
            Console.WriteLine(n3);
            Console.ReadKey();
```

输出3，因为n1和n2都是int型，计算后得到结果也是int型，即使前面n3是double，也只是一个隐式类型转换



# 第三天

## 类型转换

上面说的强制类型转换（其实还有自动类型转换，没有int转double就是，没有写出来）要求转换前和转换后的两个数据类型必须是同类的，如果这里如何想要将string类型转换成double类型，就不能用上面两种了，需要一种新的。

### Convert

```c#
            string str = "123";
            double num = Convert.ToDouble(str);
```

这样，就可以了。



来个练习：

让用户输入姓名，语文，数学，英语的三门课的成绩，然后给用户显示，xx，你的总成绩为xx分，平均成绩为xx分。

```c#
            Console.WriteLine("请输入你的姓名:");
            string strName = Console.ReadLine();
            Console.WriteLine("请输入你的语文成绩:");
            string strChinese = Console.ReadLine();
            Console.WriteLine("请输入你的数学成绩:");
            string strMath = Console.ReadLine();
            Console.WriteLine("请输入你的英语成绩:");
            string strEnglish = Console.ReadLine();

            double chinese = Convert.ToDouble(strChinese);
            double math = Convert.ToDouble(strMath);
            double english = Convert.ToDouble(strEnglish);

            Console.WriteLine("{0}，你的总成绩为：{1}，平均成绩为：{2}。", strName, chinese + math + english, (chinese + math + english) / 3);
```

上面的输出平均成绩那里会有很多位，下面介绍如何按照规定的位数输出。

```c#
            Console.WriteLine("{0}，你的总成绩为：{1}，平均成绩为：{2:0.00}。", strName, chinese + math + english, (chinese + math + english) / 3);
```

在占位符那里按照“数字:0.00"就可以保留小数点后两位输出了，其他同理。



上面那个程序还可以简写：

```c#
            Console.WriteLine("请输入你的姓名：");
            string name = Console.ReadLine();
            Console.WriteLine("请输入你的语文成绩：");
            double chinese = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine("请输入你的数学成绩：");
            double math = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine("请输入你的英语成绩：");
            double english = Convert.ToDouble(Console.ReadLine());

            Console.WriteLine("{0}，你的总成绩为：{1}，你的平均成绩为：{2:0.00}", name, chinese + math + english, (chinese + math + english) / 3);
            Console.ReadKey();
```



# 第四天

## 异常捕获

### try-catch

使用方法：

```c#
            try {
                可能出现异常的代码;
                .................;
                .................;
                .................;
                .................;
            }
            try和catch之间不能写代码;
            catch {
                出现异常后要执行的代码;
            }
```

具体实现如下：

```c#
        static void Main(string[] args) {
            bool b = true;
            int num = 0;
            try {
                Console.WriteLine("请输入数字：");
                num = Convert.ToInt32(Console.ReadLine());
            }
            catch {
                Console.WriteLine("输入的字符串不能转化成数字");
                b = false;           
            }
            if (b) {
                Console.WriteLine(num * 2);
            }
            Console.ReadKey();
        }
```



## switch-case

有点忘了，直接看练习：

李四的年终工作评定，如果定为A级，则工资涨500元，如果定为B级，则工资涨200元，如果定为C级，工资不变，如果定为D级，则工资降200元，如果定为E级工资降500元。设李四的原工资为5000元，请用户输入李四的评级，然后显示李四来年的工资。

```c#
        static void Main(string[] args) {
            bool b = true;
            decimal salary = 5000m;
            Console.WriteLine("请输入李四的评级：");
            string level = Console.ReadLine();

            switch (level) {
                case "A":
                    salary += 500;
                    break;
                case "B":
                    salary += 200;
                    break;
                case "C":
                    break;
                case "D":
                    salary -= 200;
                    break;
                case "E":
                    salary -= 500;
                    break;
                default:
                    Console.WriteLine("请输入正确的评级");
                    b = false;
                    break;
            }
            if (b) {
                Console.WriteLine("李四来年的工资为：{0}", salary);
            }
            Console.ReadKey();
        }
```

```c#
            //输入年份，月份，判断这个月有多少天
            bool b = true;
            Console.WriteLine("请输入年份：");
            try {
                int year = Convert.ToInt32(Console.ReadLine());
                Console.WriteLine("请输入月份：");
                try {
                    int month = Convert.ToInt32(Console.ReadLine());
                    int day = 0;
                    switch (month) {
                        case 1:
                        case 3:
                        case 5:
                        case 7:
                        case 8:
                        case 10:
                        case 12:
                            day = 31;
                            break;
                        case 2:
                            if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)){
                                day = 29;
                            }
                            else {
                                day = 28;
                            }
                            break;
                        default:
                            if (month >= 1 && month <= 12) {
                                day = 30;
                            }
                            else {
                                Console.WriteLine("请输入1到12月。");
                                b = false;
                            }
                            break;
                    }
                    if (b) {
                        Console.WriteLine("{0}年{1}月有{2}天。", year, month, day);
                    }
                }
                catch {
                    Console.WriteLine("请输入正确的月份。");
                }
            }
            catch {
                Console.WriteLine("请输入正确的年份。");
            }
            Console.ReadKey();
```



## do-while

这种循环有点忘了，写个例子巩固一下

```c#
           //提示用户输入用户名和密码，如果用户名不为admin或者密码不为888888，则继续输入
            string name = "";
            string pwd = "";
            do {
                Console.WriteLine("请输入用户名：");
                name = Console.ReadLine();
                Console.WriteLine("请输入密码：");
                pwd = Console.ReadLine();
            } while (name != "admin" || pwd != "888888");
            Console.WriteLine("登录成功！");
            Console.ReadKey();
```



# 第五天

## for

```c#
            for (int i = 1; i < 10; ++i) {
                for (int j = 1; j < 10; ++j) {
                    Console.Write("{0}*{1}={2}\t", i, j, i * j);
                }
                Console.WriteLine();
            }
```

就是复习下for循环，然后熟悉下转义符"\t"还有就是"WriteLine"和"Write"的区别，前者有换行的功能，后者没有  



## 类型转换

### int.Parse

前面讲过了"Convert.ToInt32"，这两个其实实现的是同一个功能，Convert.ToInt32内部实现其实调用的int.Parse，所以后int.Parse的效率会更高一点的，因为少一步调用。

### int.TryParse

看字面意思就能明白，这个是尝试转换，如果不能转换的话不会抛异常，下面来个对比：

```c#
        static void Main(string[] args) {
            int num1 = Convert.ToInt32("1");
            int num2 = int.Parse("2");
            int num3 = 0;
            bool b = int.TryParse("3", out num3);
            Console.WriteLine("num1={0},num2={1},num3={2},b={3}", num1, num2, num3, b);
            Console.ReadKey();
        }
```

总结：

* Convert.ToInt32和int.Parse都一样，如果失败了就是抛异常，前者的实现是调用的后者
* int.TryParse的使用方法和前两个不怎么一样，主要原因是这个函数不会抛出异常，所以返回的结果是一个bool类型，如果成功为true，如果失败为false，所以还得提供参数用来存储转换后的值，也就是上面的num3。注意，如果转换失败了，num3的值将会被赋值为0。如果有兴趣，把num3的初值换个试下就行。



## continue

这个平时用的比较少，复习一下：

计算1到100中除了能被7整之外的所有数的和。

```c#
        static void Main(string[] args) {
            int sum = 0;
            for (int i = 1; i <= 100; i++) {
                if (i % 7 == 0) {
                    continue;
                }
                sum += i;
            }
            Console.WriteLine(sum);
            Console.ReadKey();
        }
```



# 第六天

## 枚举

枚举是一个变量类型，使用枚举的原因是为了能够规范化命名，使编程变量统一。

枚举就是一个变量类型，只是枚举声明、赋值、使用的方式跟那些普通的的变量类型不一样。

**基本语法：**

[public] enum 枚举名 {

​			值1，

​			值2，

​			值3，

​			......

}

public：访问修饰符，公开的，公共的，哪都可以访问。

enum：关键字，声明枚举的关键字

枚举名：要符合Pascal命名规范

```c#
namespace _01_枚举 {
    class Program {
        public enum Gender {
            男,
            女
        }
        static void Main(string[] args) {
            Gender gender = Gender.男;
            Console.WriteLine("性别为{0}", gender);
            Console.ReadKey();
        }
    }
}
```

注意：将枚举声明到命名空间的下面，类的外面，表示在这个命名空间下，所有的类都可以使用这个枚举。



##  枚举和int以及string类型之间的转换

### 和int之间

```c#
namespace _02_枚举和int以及string类型之间的转换 {
    public enum QQstate {
        OnLine = 10,
        OffLine,
        Leave = 9,
        Busy,
        QMe
    }
    class Program {
        static void Main(string[] args) {
            Console.WriteLine((int)QQstate.OnLine);
            Console.WriteLine((int)QQstate.OffLine);
            Console.WriteLine((int)QQstate.Leave);
            Console.WriteLine((int)QQstate.Busy);
            Console.WriteLine((int)QQstate.QMe);
            Console.ReadKey();
        }
    }
}
```

对应的输出结果分别为10，11，9，10，11

**那么问题来了，如果我将这五个数字转换成对应的QQstate会是怎么样，下来来试一下**

```c#
namespace _02_枚举和int以及string类型之间的转换 {
    public enum QQstate {
        OnLine = 10,
        OffLine,
        Leave = 9,
        Busy,
        QMe
    }
    class Program {
        static void Main(string[] args) {
            Console.WriteLine((QQstate)10);
            Console.WriteLine((QQstate)11);
            Console.WriteLine((QQstate)9);
            Console.WriteLine((QQstate)10);
            Console.WriteLine((QQstate)11);
            Console.ReadKey();
        }
    }
}
```

**对应的输出是Busy，OffLine，Leave，Busy，OffLine，可以看出，和上面的并不对应，至于为什么会这样，我也不知道了，以后慢慢研究。**

**总结**

- 枚举类型默认是和int类型相互兼容的，所以可以通过强制转换类型的语法互相转换。
- 当转换一个枚举中没有的值时，不会抛异常，而是直接将数字显示出来。



### 和string之间

**所有类型都能转换成字符串，调用的是函数ToString()。**

```c#
namespace _02_枚举和int以及string类型之间的转换 {
    public enum QQstate {
        OnLine = 10,
        OffLine,
        Leave = 9,
        Busy,
        QMe
    }
    class Program {
        static void Main(string[] args) {
            int n1 = 10;
            double n2 = 3.14;
            decimal n3 = 4000m;
            QQstate state = QQstate.OnLine;

            string s1 = n1.ToString();
            string s2 = n2.ToString();
            string s3 = n3.ToString();
            string s4 = state.ToString(); 
            Console.WriteLine("{0}\n{1}\n{2}\n{3}", s1, s2, s3,s4);
            Console.ReadKey();
        }
    }
}
```

结果省略，反正就是可以。

如何将string类型转换成枚举类型，代码如下，有点复杂

```c#
namespace _02_枚举和int以及string类型之间的转换 {
    public enum QQstate {
        OnLine = 10,
        OffLine,
        Leave = 9,
        Busy,
        QMe
    }
    class Program {
        static void Main(string[] args) {

            string s = "11";
            QQstate state = (QQstate)Enum.Parse(typeof(QQstate), s);
            Console.WriteLine(state);
            Console.ReadKey();
        }
    }
}
```

输出结果是OfflLine，同样的问题，有重复的时候如何确定不知道了。

**总结**

* 枚举同样也可以和sting类型互相转换，如果将枚举类型转换成string类型，则直接调用ToString()

* 如果将字符串转换成枚举类型则需要下面这样一行代码：

  (要转换的枚举类型)Enum.Parse(typeof(要转换的枚举类型)),"要转换的字符串");

* 如果转换的字符串是数字，则就算枚举中没有，也不会抛异常
* 如果转换的字符串是文本，如果枚举中没有，就会抛出异常



## 结构

和C++里面的结构差不多，直接上代码，注意后面需要注意的地方。

```c#
namespace _03_结构 {
    public enum Gender {
        男,
        女
    }
    public struct Person {
        public string _name;  //字段
        public int _age;
        public char _gender;
    }
       class Program {
        static void Main(string[] args) {
            Person zsPerson;
            zsPerson._name = "张三";
            zsPerson._age = 21;
            zsPerson._gender = (char)Gender.男;

            Person lsPerson;
            lsPerson._name = "李四";
            lsPerson._age = 22;
            lsPerson._gender = (char)Gender.女;

            Console.WriteLine(zsPerson._name);
            Console.WriteLine(lsPerson._name);
            Console.ReadKey();
        }
    }
}
```

**注意：**

* 结构前面也是需要加例如public之类的，估计和类差不多

* 结构中的字段如果想要外界访问到，前面也是得加上public，和C++中的类不怎么一样

* 结构中的变量不叫变量，叫字段，前面需要加上"_"用以区分

这里有一个问题，就是那个不知道为什么那个性别那里需要加上(char)转换，明明都是char类型的，暂时没有想明白。



## 数组

直接看一下代码

```c#
namespace _04_数组 {
    class Program {
        static void Main(string[] args) {
            int[] nums = new int[10];
            for (int i = 0; i < nums.Length; ++i) {
                nums[i] = i;
            }
            for (int j = 0; j < nums.Length; ++j) {
                Console.WriteLine(nums[j]);
            }
            Console.ReadKey();
        }
    }
}
```

没有什么好说的，就是有一些需要注意一下：

* int等数字的数组，里面的初值都是"0"；
* bool类型的数组，里面的初值都是"false"；
* string类型的数组，里面的初值都是"null"，这里的null和空值是不一样的，null表示还没有在内存中开辟空间，空的表示已经开辟了空间了。

下面还有一些其他声明方式，看下代码：

```c#
            int[] nums = new int[10];
            int[] numsTwo = { 1, 2, 3 };
            int[] numsThree = new int[3] { 1, 2, 3 };
            int[] numsFour = new int[] { 1, 2, 3 };
```

和上面那种介绍过的一起总共用四种方式，一般只用前两种。



## 排序

### 冒泡

先来个最基本的冒泡

```c#
namespace _06_冒泡排序 {
    class Program {
        static void Main(string[] args) {
            int[] nums = { 1, 9, 3, 6, 5, 8, 7, 2, 4 };
            for (int i = 0; i < nums.Length - 1; ++i)
                for (int j = 0; j < nums.Length - i - 1; ++j) {
                    if (nums[j] > nums[j+1]){
                        nums[j] ^= nums[j + 1];
                        nums[j + 1] ^= nums[j];
                        nums[j] ^= nums[j + 1];
                    }
                }
            for (int k = 0; k < nums.Length; ++k) {
                Console.WriteLine(nums[k]);
            }
            Console.ReadKey();
        }
    }
}
```



### Sort和Reverse

自带的两个函数，前面是按照升序排列，后面是倒序排列

# 第七天

## 方法(函数)

书写方法和C++中有点不一样，要多写

```c#
namespace _07_方法_函数_ {
    class Program {
        static void Main(string[] args) {
            int n1 = 2, n2 = 3;
            int max = Program.GetMax(n1, n2);
            Console.WriteLine(max);
            Console.ReadKey();
        }
        /// <summary>
        /// 计算两个整数之间的最大值并且将最大值返回
        /// </summary>
        /// <param name="n1">第一个整数</param>
        /// <param name="n2">第二个整数</param>
        /// <returns></returns>
        public static int GetMax(int n1, int n2) {
            return n1 > n2 ? n1 : n2;
        }
    }
}
```

注意写注释，养成好习惯。

注意：

* 函数的使用方式是需要前面写上类名的，例如Console.WriteLine()，这个函数，它就是在Console这个类中
* 前面的类名可以省略，如果使用该函数的地方和函数在一个类中，就可以省略。



### 静态字段(用来模拟全局变量)

在C#中没有全局变量，所以需要使用静态字段的方式在来模拟全局变量

```c#
namespace _01_函数 {
    class Program {
        public static int _number = 10;  //使用字段来模拟全局变量
        static void Main(string[] args) {
            bool b = IsLeap(2000);
            Console.WriteLine(b);
            Console.ReadKey();
        }
        /// <summary>
        /// 判断一个年份是否是闰年
        /// </summary>
        /// <param name="year">传入的年份</param>
        /// <returns>返回是否是闰年</returns>
        public static bool IsLeap(int year) {
            bool b = (year % 400 == 0) || (year % 4 == 0 && year % 100 != 0);
            return b;
        }
    }
}
```



### 函数练习

```c#
namespace _02_函数练习 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入一个数字：");
            string s = Console.ReadLine();
            int number = GetNumber(s);
            Console.WriteLine(number);
            Console.ReadKey();
        }
        /// <summary>
        /// 将输入的字符串转换成数字，如果不是数字，提示重新输入
        /// </summary>
        /// <param name="s">输入的字符串</param>
        /// <returns>转换后的数字</returns>
        public static int GetNumber(string s) {
            while (true) {
                try {
                    int number = Convert.ToInt32(s);
                    return number;
                }
                catch {
                    Console.WriteLine("输入有误，请重新输入！");
                    s = Console.ReadLine();
                }
            }
        }
    }
}
```

```c#
namespace _02_函数练习 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入Yes或者No:");
            string s = Console.ReadLine();
            s = IsYesOrNo(s);
            Console.WriteLine(s);
            Console.ReadKey();
        }
        /// <summary>
        /// 限定用户只能输入Yes或者No，并且返回
        /// </summary>
        /// <param name="s">用户的输入</param>
        /// <returns>返回Yes或者No</returns>
        public static string IsYesOrNo(string s) {
            while (true) {
                if (s == "Yes" || s == "No") {
                    return s;
                }
                else {
                    Console.WriteLine("请重新输入：");
                    s = Console.ReadLine();
                }
            }
        }
    }
}
```



## 函数中的高级参数

### out参数 

* 如果在一个函数中，返回多个相同类型的值的时候，可以考虑返回一个数组
* 如果在一个函数中，返回不同类型的值的时候，可以考虑使用out参数

使用方法如下：

```c#
namespace _03_out参数 {
    class Program {
        static void Main(string[] args) {
            int[] nums = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
            int inputMax;
            int inputMin;
            int inputSum;
            int inputAvg;
            string inputS;
            OutTest(nums, out inputMax, out inputMin, out inputSum, out inputAvg, out inputS);

            Console.WriteLine("最大值为{0},最小值为{1},总和为{2},平均值为{3},字符串为{4}", inputMax, inputMin, inputSum, inputAvg, inputS);
            Console.ReadKey();
        }

        public static void OutTest(int[] nums,out int max,out int min,out int sum,out int avg,out string s) {
            max = int.MinValue;
            min = int.MaxValue;
            sum = 0;
            for (int i = 0; i < nums.Length; ++i) {
                if (max < nums[i]) {
                    max = nums[i];
                }
                if (min > nums[i]) {
                    min = nums[i];
                }
                sum += nums[i];
            }
            avg = sum / nums.Length;
            s = "孙浩天";
        }
    }
}
```

这里有几点需要注意一下：

* 在用out参数的时候，在形参列表已经声明过变量，在具体实现中不能再写了
* 在输出的时候所有的out参数必须有值
* 在调用函数之前，参数不必赋值，因为在调用参数的时候，会给参数进行赋值的。
* 不用写ruturn，这是我最初的理解，后来发现理解错误，是可以写return的

练习2：

```c#
namespace _03_out参数 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入用户名:");
            string userName = Console.ReadLine();
            Console.WriteLine("请输入密码:");
            string userPwd = Console.ReadLine();
            string msg;
            bool b = IsLogin(userName, userPwd, out msg);
            Console.WriteLine("登录信息{0},{1}", b, msg);
            Console.ReadKey();
        }
        /// <summary>
        /// 判断用户是否登录成功
        /// </summary>
        /// <param name="name">用户名</param>
        /// <param name="pwd">用户密码</param>
        /// <param name="msg">多余返回的登录信息</param>
        /// <returns>是否登录成功</returns>
        public static bool IsLogin(string name,string pwd, out string msg) {
            if(name == "admin" && pwd == "888888") {
                msg = "登录成功";
                return true;
            }
            else if (name == "admin") {
                msg = "密码错误";
                return false;
            }
            else if (pwd == "888888") {
                msg = "用户名错误";
                return false;
            }
            else {
                msg = "你胡乱输的吧";
                return false;
            }
        }
    }
}
```

练习3，实现自己的int.TryParse：

```c#
namespace _03_out参数 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入一个数字：");
            string s = Console.ReadLine();
            int res;
            bool b = MyIntTryParse(s, out res);
            Console.WriteLine("转换是否成功:{0},转换结果:{1}", b, res);
            Console.ReadKey();
        }
        public static bool MyIntTryParse(string s, out int res) {
            try {
                res = Convert.ToInt32(s);
                return true;
            }
            catch {
                res = 0;
                return false;
            }
        }
    }
}
```

这样，就理解了原本为什么前面要加上一个out了，其实就是就是用了out参数



### ref参数

能够将一个变量带入一个函数中，同时可以将这个参数的值改变，其实也就是原本C++里面的指针或者引用。

来，看下代码：

```c#
namespace _04_ref参数 {
    class Program {
        static void Main(string[] args) {
            int n1 = 10;
            int n2 = 20;
            int n3 = 30;
            int n4 = 40;
            Swap1(n1, n2);
            Swap2(ref n3, ref n4);
            Console.WriteLine("交换后的n1 = {0}, n2 = {1}", n1, n2);
            Console.WriteLine("交换后的n3 = {0}, n4 = {1}", n3, n4);
            Console.ReadKey();
        }
        public static void Swap1(int num1, int num2) {
            num1 ^= num2;
            num2 ^= num1;
            num1 ^= num2;
        }
        public static void Swap2(ref int num1, ref int num2) {
            num1 ^= num2;
            num2 ^= num1;
            num1 ^= num2;
        }
    }
}
```

上面的代码，n1和n2的值没有交换，n3和n4的值交换了。



### params参数

将实参列表中跟可变数组类型一致的元素都当作数组的元素去处理，来，看下代码。

```c#
namespace _05_params参数 {
    class Program {
        static void Main(string[] args) {
            string name1 = "刘奥琦";
            string name2 = "孙浩天";
            string name3 = "蜜蜜";
            int[] nums = { 1, 2, 3 };
            Test1(name1, nums);
            //之后的两次调用都可以不用写出数组，直接给出int类型的参数，会直接当成int[]数组去处理
            Test2(name2, 100, 100, 100);
            Test2(name3, 1, 2, 3, 4, 5, 6, 7, 8, 9);
        }
        public static void Test1(string name, int[] nums) {
            int sum = 0;
            for (int i = 0; i < nums.Length; ++i) {
                sum += nums[i];
            }
            Console.WriteLine("{0}的总成绩是：{1}", name, sum);
        }
        public static void Test2(string name, params int[] nums) {
            int sum = 0;
            for (int i = 0; i < nums.Length; ++i) {
                sum += nums[i];
            }
            Console.WriteLine("{0}的总成绩是：{1}", name, sum);
        }
    }
}
```

* 这里如果在调用函数的时候给出double类型的参数，会报错。
* 可是如果我想再多加一个参数呢，例如学号，来看下代码

```c#
namespace _05_params参数 {
    class Program {
        static void Main(string[] args) {
            string name1 = "刘奥琦";
			//001会识别成id，后面的3个100识别成nums数组中的内容。
            Test3(name1, 001, 100, 100, 100);
        }
        public static void Test3(string name, int id, params int[] nums) {
            int sum = 0;
            for (int i = 0; i < nums.Length; ++i) {
                sum += nums[i];
            }
            Console.WriteLine("{0}的学号是：{1}，总成绩是：{2}", name, id, sum);
        }
    }
}
```

**总结，在使用params参数时候，必须放在参数列表的最后。**



## 函数的重载

指的就是函数的名称相同，只是传入的参数不同，从而实现不同的效果。

* 如果参数的个数相同，那么参数的类型就不能相同
* 如果参数的类型相同，那么参数的个数就不能相同
* 函数的重载和返回值类型没有关系

```c#
namespace _06_函数的重载 {
    class Program {
        static void Main(string[] args) {
            int n1 = 10, n2 = 20;
            double n3 = 10.0, n4 = 20.0;
            int res1 = Test(n1, n2);
            double res2 = Test(n3, n4);
            Console.WriteLine("{0},{1}",res1,res2);
            Console.ReadKey();
        }
        public static int Test(int n1, int n2) {
            return n1 + n2;
        }
        public static double Test(double n1, double n2) {
            return n1 + n2;
        }
    }
}
```



## 函数的递归

函数自己调用自己，面试的时候也问了我这个问题。



## 总结练习

```c#
namespace _07_综合练习 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入第一个数字:");
            string strNum1 = Console.ReadLine();
            int num1 = GetNum(strNum1);
            Console.WriteLine("请输入第二个数字：");
            string strNum2 = Console.ReadLine();
            int num2 = GetNum(strNum2);
            JudgeNum(ref num1, ref num2);
            int sum = GetSum(num1, num2);
            Console.WriteLine("输入的数字1为：{0}，数字2为：{1}，总和为：{2}", num1, num2, sum);
            Console.ReadKey();
        }
        /// <summary>
        /// 将传入的字符串转换成数字，如果不对重新输入
        /// </summary>
        /// <param name="s">传入的字符串</param>
        /// <returns>转换后的数字</returns>
        public static int GetNum(string s) {
            int num;
            while (true) {
                try {
                    num = Convert.ToInt32(s);
                    return num;
                }
                catch {
                    Console.WriteLine("请重新输入数字：");
                    s = Console.ReadLine();
                }
            }
        }
        /// <summary>
        /// 判断数字1是否满足小于数字2
        /// </summary>
        /// <param name="n1">数字1</param>
        /// <param name="n2">数字2</param>
        public static void JudgeNum(ref int n1,ref int n2) {
            while (true) {
                if (n1 < n2) {
                    return;
                }
                else {
                    Console.WriteLine("要求第一个数字小于第二个数字，请重新输入第一个数字：");
                    string s1 = Console.ReadLine();
                    n1 = GetNum(s1);
                    Console.WriteLine("要求第一个数字小于第二个数字，请重新输入第二个数字：");
                    string s2 = Console.ReadLine();
                    n2 = GetNum(s2);
                }
            }
        }
        /// <summary>
        /// 从数字1累加到数字2，输出和
        /// </summary>
        /// <param name="n1"></param>
        /// <param name="n2"></param>
        /// <returns></returns>
        public static int GetSum(int n1, int n2) {
            int sum = 0;
            for (int i = n1; i <= n2; ++i) {
                sum += i;
            }
            return sum;
        }
    }
}
```



# 第八天

## 飞行棋



# 第九天

## 对象 

这里的创建对象的语法和C++中不同，还有这里的字段和属性的关系要注意，C++中并没有字段。

看下代码：

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _01_面向对象概念 {
    class Program {
        static void Main(string[] args) {
            Person miMi = new Person();
            miMi.Name = "刘奥琦";
            miMi.Age = 27;
            miMi.Gender = '神';
            miMi.Test();
            Console.ReadKey();
        }
    }
}
```

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _01_面向对象概念 {
    class Person {
        
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }

        private int _age;
        public int Age {
            get { return _age; }
            set {
                if (value < 0 || value > 100) {
                    value = 18;
                }
                _age = value;
            }
        }

        private char _gender;
        public char Gender {
            get {
                if (_gender != '男' && _gender != '女') {
                    _gender = '女';
                }
                return _gender;
            }
            set { _gender = value; }
        }

        public void Test() {
            Console.WriteLine("我叫{0}，我今年{1}岁了，我是{2}生，我爱孙浩天啦", this.Name, this.Age, this.Gender);
        }
    }
}
```

上面是主函数，下面是类，说几个需要注意的点，其实也就是属性：

* 属性的作用就是保护字段，对字段的赋值和取值进行限定
* 属性的本质就是两个方法，一个叫get()，一个叫set()



## 静态和非静态

主要区别：

* 在非静态类中，既可以有实例成员，也可以有静态成员

* 静态成员必须使用类名去调用，而实例成员使用对象名调用

* 静态函数中，只能访问静态成员，不允许访问实例成员

* 实例函数中，既可以使用静态成员，也可以使用实例成员

* 静态类中只允许有静态成员，不允许出现实例成员

* 静态类不能创建实例  

使用场景：

* 如果你想要你的类当作一个“工具类”去使用，这个时候可以考虑将类写成静态类
* 静态类在整个项目中资源共享

前面说过，普通的类是不占内存的，但是静态类需要占内存，内存分为堆、栈、静态存储区域，静态类就是放在静态存储区域。



## 构造函数

创建对象的语法：类名 对象名 = new 类名()

* 构造函数没有返回值，连void也不能写
* 构造函数的名称必须和类名一样
* 构造函数是可以重载的
* 类当中是有一个默认的无参数的构造函数，当写了一个新的构造函数之后，不管是有参数的还是无参数的，默认的构造函数都没有了





## new

还是上面那个语法：类名 对象名 = new 类名()

此时，这个new做了3件事：

* 在内存中开辟了一块空间
* 在开辟的空间中创建对象
* 调用对象的构造函数进行初始化对象



## this

this有两个作用，一个是指对象本身，另一个是显示地调用该对象的构造函数，代码如下：

```c#
namespace _03_构造函数 {
    public class Student {
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }

        private int _age;
        public int Age {
            get { return _age; }
            set { _age = value; }
        }

        private char _gender;
        public char Gender {
            get { return _gender; }
            set { _gender = value; }
        }

        private int _chinese;
        public int Chinese {
            get { return _chinese; }
            set { _chinese = value; }
        }

        private int _math;
        public int Math {
            get { return _math; }
            set { _math = value; }
        }

        private int _english;
        public int English {
            get { return _english; }
            set { _english = value; }
        }

        public Student(string name,int age,char gender,int chinese,int math,int english) {
            this.Name = name;
            this.Age = age;
            this.Gender = gender;
            this.Chinese = chinese;
            this.Math = math;
            this.English = english;
        }
        //这里为了不再写一遍那些冗余的代码，使用this调用这个对象的构造函数
        public Student(string name,int chinese,int math, int english) : this(name, 0, 'c', chinese, math, english) { }
    }
}
```



## 析构函数

和C++中的析构函数差不多，但是因为C#中引入了GC机制，所以效果不是很大了，除非你想立马回收



# 第十天

##　命名空间

可以认为类是属于命名空间的，如果在当前项目中没有这个类的命名空间，需要我们手动的导入这个类所在的命名空间，有两种方法：

* 用鼠标去点
* alt+shift+F10
* 记住命名空间，手动的去引用

如何在一个项目中引用另一个项目的类：

* 添加引用
* 引用命名空间



## 值类型和引用类型

区别：

* 值类型和引用类型在内存上存储的地方不一样
  * 值类型的值是存储在内存的栈上
  * 引用类型的值是存储在内存的堆上
* 在传递值类型和传递引用类型的时候，传递的方式不一样
  * 值类型称为值传递
  * 引用类型称为引用传递

* 目前学过的值类型和引用类型有：
  * 值类型：int、double、bool、char、decimal、struct、enum
  * 引用类型：数组、string、自定义类、集合、object、接口

这里插入一个网址：[深入理解值类型和引用类型](https://www.cnblogs.com/zhanlang/p/9603592.html)



## 字符串的不可变性

当给一个字符串重新赋值之后，原本的值并没有被销毁，而是在堆中重新开辟了一块看得见存储新值，当程序结束后，GC扫描整个内存，如果发现有的空间没有被指向，就立即销毁。

说一下这个是怎么回事：就是如果定义了一个字符串string name = "刘奥琦"，这个时候在堆中存的是“刘奥琦”，在栈中存的是name以及“刘奥琦”在堆中所在的地址，之后让name = "蜜蜜"，堆中会重新开辟一块空间存储“蜜蜜”，然后在栈中将地址变更为“蜜蜜“所在的地址。

还有一种情况如果定义了string s1 = "123"，string s2 = "123"，这个时候在堆中只会开辟一块空间存储"123"，然后在s1和s2存储的地址同时指向堆中的这个地址，因为字符串的不可变性，这也就避免了如果s1="321"之后，s2也跟着改变。

string类型可以看作是char类型的一个只读数组，所以我们可以通过下标去访问字符串中的某一个元素。但是是不能改变，如果想要改变需要先将string类型转换成char[]类型，下面看一下代码：

```c#
namespace _02_字符串的不可变性 {
    class Program {
        static void Main(string[] args) {
            string s = "abc";
            Console.WriteLine(s[0]);
            //s[0] = 'b';          //只读的，不能赋值
            char[] chs = s.ToCharArray();
            chs[0] = 'b';
            s = new string(chs);   //将字符数组转换成字符串
            Console.WriteLine(s[0]);
            Console.WriteLine(s);
            Console.ReadKey();
        }
    }
}
```



## StringBuilder

通过字符串的不可变性，已经知道如果需要重复对一个string类型赋值，会占用很多内存和时间，所以需要使用StringBuilder。这个相当于始终在原本的那个字符串上操作，但是如果想输出的话，当时得转换成string类型。

```c#
namespace _02_字符串的不可变性 {
    class Program {
        static void Main(string[] args) {
            string s1 = null;
            Stopwatch sw1 = new Stopwatch();  //创建一个对象用来计时
            sw1.Start(); //计时开始
            for (int i = 0; i < 100000; ++i) {
                s1 += i;
            }
            sw1.Stop();  //计时结束
            Console.WriteLine(sw1.Elapsed);   //输出这个时间，记住单词elspsed

            StringBuilder s2 = new StringBuilder();
            Stopwatch sw2 = new Stopwatch();
            sw2.Start();
            for (int i = 0; i < 100000; ++i) {
                s2.Append(i);
            }
            sw2.Stop();
            Console.WriteLine(sw2.Elapsed);
            Console.WriteLine(s2.ToString());  //如果想要输出还是得转换成string类型
            Console.ReadKey();
        }
    }
}
```



## 字符串中提供的常用方法

### Length

获取当前字符串中字符的个数

```c#
	string str = "abc";
	int len = str.Length;
```



### ToUpper()，ToLower()

分别是将字符串转换成大写形式和小写形式



### Equals()

比较两个字符串是否相等

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string s1 = "abc";
            string s2 = "ABC";
            //这里的StringComparison是一个枚举类型，可以选择比较方式
            if (s1.Equals(s2, StringComparison.CurrentCultureIgnoreCase)) {
                Console.WriteLine("在不考虑大小写的情况下，s1等于s2");
            }
            else {
                Console.WriteLine("在不考虑大小写的情况下，s1也不等于s2");
            }
            Console.ReadKey();
        }
    }
}
```

上面输出的结果就是相等。



### Split()

分割字符串，返回字符串类型的数组，即string[]类型

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "a,b.c/d e";
            //想要去掉哪些元素，就在char[]写出来
            char[] chs = { ',', '.', '/', ' ' };
  
            string[] newStr1 = str.Split(chs,StringSplitOptions.None);
            for (int i = 0; i < newStr1.Length; ++i) {
                Console.Write(newStr1[i]);
            }

            Console.WriteLine();

            string[] newStr2 = str.Split(chs, StringSplitOptions.RemoveEmptyEntries);
            for (int i = 0; i < newStr2.Length; ++i) {
                Console.Write(newStr2[i]);
            }
            Console.ReadKey();
        }
    }
}
```

这里视频里面说如果不写后面的那个StringSplitOptions.RemoveEmptyEntries的话，返回的字符串数组中会有很多null，但是我试了一下，并没有，是后来又改了吗？



### Contains()

检测字符串中是否有相应的子串，返回类型为bool



### Replace()

替换相应的子串

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "国家主席孙浩天";
            if (str.Contains("孙浩天")) {
                str = str.Replace("孙浩天", "刘奥琦");  //注意，这里前面需要一个字符串接收
            }
            Console.WriteLine(str);
            Console.ReadKey();
        }
    }
}
```



### Substring()

截取字符串，在截取的时候包含截取的那个位置

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "abcdefg";
            string subStr = str.Substring(0, 2);//前面是初始下标，后面是大小
            Console.WriteLine(subStr);
            Console.ReadKey();
        }
    }
}
```



### StartWith() EndsWith()

分别是判断是否以相应的字符串开头或者结尾，返回类型为bool

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "abcdefg";
            if (str.StartsWith("ab")) {
                Console.WriteLine("是以ab开头的");
            }
            else {
                Console.WriteLine("不是以ab开头的");
            }

            if (str.EndsWith("g")) {
                Console.WriteLine("是以g结尾的");
            }
            else {
                Console.WriteLine("是以g结尾的");
            }
            Console.ReadKey();
        }
    }
}
```



### IndexOf()

判断某个字符串在字符串中第一次出现的位置，如果没有返回-1

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
			string str = "abbcdefg";
            int index = str.IndexOf("b");
            Console.WriteLine(index);
            Console.ReadKey();
        }
    }
}
```



### LastIndexOf()

判断某个字符串在字符串中最后一次出现的位置，如果没有返回-1

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "abcddefg";
            int index = str.LastIndexOf("d");
            Console.WriteLine(index);
            Console.ReadKey();
        }
    }
}
```



### Trim()

去掉字符串中前后的空格，同时还有TrimEnd()和TrimStart()，分别是去掉后面和前面的空格

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = "   abc   ";
            string str1 = str.Trim();
            string str2 = str.TrimStart();
            string str3 = str.TrimEnd();
            Console.WriteLine(str1);
            Console.WriteLine(str2);
            Console.WriteLine(str3);
            Console.ReadKey();
        }
    }
}
```



### string.IsNullOrEmpty()

判断一个字符串是否为空，或者null，返回类型为bool类型，这里需要注意一下string str = " "，这里的str并不是空的，只有当str = ""的时候才是空的

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string str = null;
            string str1 = "";
            string str2 = " ";
            if (string.IsNullOrEmpty(str)) {
                Console.WriteLine("是空的");
            }
            else {
                Console.WriteLine("不是空的");
            }
            if (string.IsNullOrEmpty(str1)) {
                Console.WriteLine("是空的");
            }
            else {
                Console.WriteLine("不是空的");
            }
            if (string.IsNullOrEmpty(str2)) {
                Console.WriteLine("是空的");
            }
            else {
                Console.WriteLine("不是空的");
            }
            Console.ReadKey();
        }
    }
}
```



### string.Join()

将数组按照指定的字符串连接，返回一个字符串

```c#
namespace _03_字符串中提供的常用方法 {
    class Program {
        static void Main(string[] args) {
            string[] str = { "a", "b", "c" };
            string newStr = string.Join("|", str);
            Console.WriteLine(newStr);
            Console.ReadKey();
        }
    }
}
```



## 继承

首先需要说一下，Object是所有类的父类

* 子类继承了父类的属性和方法，但是没有继承父类的私有字段，虽然在内存中可以看到
* 子类并没有继承父类的构造函数，但是在创建子类的时候，子类会默认调用父类的无参数的构造函数，创建一个父类对象，以让子类能够使用父类中的成员。所以，如果在父类中重新谢了写了一个有参数的构造函数之后，那个无参数的构造函数没有了，子类就调用不到了，所以子类会报错。解决方法：
  * 在父类中重新写一个无参数的构造函数
  * 在子类中显示的调用父类的构造函数(有参数的那个)，使用关键字:base()

继承的特性：

* 继承的单根性：一个子类只能有一个父类(这个和C++中不一样，C++可以交叉继承)
* 继承的传递性：就是说可以一直往下继承

下面看一下代码：

父类：

```c#
namespace _04_继承 {
    public class Person {
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }

        private int _age;
        public int Age {
            get { return _age; }
            set { _age = value; }
        }

        private char _gender;
        public char Gender {
            get { return _gender; }
            set { _gender = value; }
        }

        public Person(string name, int age, char gender) {
            this.Name = name;
            this.Age = age;
            this.Gender = gender;
        }
    }
}
```

子类：

```c#
namespace _04_继承 {
    public class Student : Person {
        private int _id;
        public int Id {
            get { return _id; }
            set { _id = value; }
        }

        public Student(string name,int age,char gender,int id) : base(name, age, gender) {
            Id = id;
        }
    }
}
```

主函数：

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _04_继承 {
    class Program {
        static void Main(string[] args) {
            Student mimi = new Student("刘奥琦", 18, '女', 2017010029);
            Console.WriteLine("{0}今年{1}岁，性别{2}，学号是{3}", mimi.Name, mimi.Age, mimi.Gender, mimi.Id);
            Console.ReadKey();
        }
    }
}
```

需要注意的就是那个使用父类的构造函数的语法，base()，这个里面不用再写string，int之类的东西了。



## new隐藏父类成员

这种情况就是说如果父类和子类中有同名的函数，子类在调用函数的时候，是调用的自身的函数，但是这种会有警告，为了解决这个问题，在子类的函数返回值前加一个new，这样就可以解决了。

父类：

```c#
namespace _05_new隐藏父类成员 {
    public class Person {
        public void SayHello() {
            Console.WriteLine("你好，我是人");
        }
    }
}
```

子类：

```c#
namespace _05_new隐藏父类成员 {
    public class Student : Person {
        public new void SayHello() {
            Console.WriteLine("你好，我是学生");
        }
    }
}
```

主函数：

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _05_new隐藏父类成员 {
    class Program {
        static void Main(string[] args) {
            Student mimi = new Student();
            mimi.SayHello();
            Console.ReadKey();
        }
    }
}
```



# 第十一天

## 里氏转换

* 子类可以赋值给父类：如果有一个地方需要一个父类作为参数，我们可以将一个子类代替父类。使用场景，前面介绍的String.Join()这个函数，要求传入的第二个参数是object[] ()，这里的object就是所有的父类，我们可以传入string类型的数，也是没有问题的。
* 如果父类中装的是子类对象，那么可以将这个父类强转为子类对象，判断转换是否成功有两种方法：
  * is：如果能够转换成功，返回true，否则返回false
  * as：如果转换成功返回对应的类型，如果失败返回null

```c#
namespace _01_里氏转换语法和练习 {
    class Program {
        static void Main(string[] args) {
            //第一种用子类代替父类的方法
            Student student1 = new Student();
            Person person1 = student1;
            //第二中用子类代替父类的方法，也就是第一种的简写
            Person person2 = new Student();

            //is的用法, 这里就转换成功了，因为person1内部装的就是Student类
            if(person1 is Student) {
                Student student2 = (Student)person1;
                student2.StudentSayHello();
                Console.WriteLine("转换成功");
            }
            else {
                Console.WriteLine("转换失败");
            }
            //这里就转换失败了，因为person2内部不是Teacher类，是Student类
            if(person2 is Teacher) {
                Teacher teacher2 = (Teacher)person2;
                teacher2.TeacherSayHello();
                Console.WriteLine("转换成功");
            }
            else {
                Console.WriteLine("转换失败");
            }

            //as的用法,student3是Student类，teacher3就是null
            Student student3 = person1 as Student;
            Teacher teacher3 = person1 as Teacher;

            Console.ReadKey();
        }
    }
}
```



## protected访问修饰符

这个和private的区别就是，private只有在当前类的内部可以访问到，在这个类的子类中都无法访问，而protected可以在当前类的自身和子类中访问到。



## ArrayList集合

这个ArrayList和数组差不多，区别就是这个可以插入任意类型的元素，而且长度可以任意改变，命名空间为

### Count

返回元素的个数，需要注意的是，如果添加int[] {1,2,3}这种类型的，个数应该加3

### Add()

添加单个元素

### AddRange()

添加集合元素，可以插入数组之类的

### Clear()

清空所有元素

### Remove()

删除单个元素，写谁就删除谁

### RemoveAt()

根据下标去删除元素

### RemoveRange()

根据下标去删除一定范围的元素

### Sort()

升序排列，这里要求所有的元素类型相同，并且是可以比较的

### Reverse()

反转

### Insert()

在指定的位置插入一个元素

### InsertRange()

在指定的位置插入一个数组

### Contaions()

判断是否有相应的元素

代码

```
namespace _03_ArrayList集合 {
    class Program {
        static void Main(string[] args) {
            ArrayList list = new ArrayList();
            list.Add(1);
            list.Add("mimi");
            list.Add('c');
            list.Add(5000m);
            int[] nums = { 1, 2, 3 };
            list.AddRange(nums);
            list.Remove(1);
            list.RemoveAt(0);
            list.RemoveRange(1, 2);                     //前面是删除的启始坐标，后面是大小
            list.Insert(0, 2);                          //前面是插入的位置，下面是插入的数据
            list.InsertRange(1, new int[] { 3, 2, 1 }); //这种插入数组的方式总是忘，记住
            if (!list.Contains("tian")) {
                list.Add("tian");
            }
            else {
                Console.WriteLine("已经有了");
            }
            for (int i = 0; i < list.Count; ++i) {
                Console.WriteLine(list[i]);
            }
            int a = (int)list[0];                      //这个如果想取出来用的话，需要进行类型转换

            Console.ReadKey();
        }
    }
}
```



### 集合的长度问题

可以通过两个变量查看，一个是Count，一个是Capcity，在初始的时候，两个数据都是0，之后为（1、4），（2、4），（3、4），（4、4)，（5、8），（6、8），（7、8），（8、8），（9、16），也就是说当实际包含的元素个数超过了可以包含的元素的个数的时候，集合就会向内存中申请多开辟一倍的空间，来保证集合的长度一直够用。

```c#
namespace _04_ArrayList集合长度的问题 {
    class Program {
        static void Main(string[] args) {
            System.Collections.ArrayList list = new System.Collections.ArrayList();
            for (int i = 0; i < 100; ++i) {
                Console.WriteLine("集合中实际个数为：{0},可以包含的元素个数为：{1}", list.Count, list.Capacity);
                list.Add(i);
            }
            Console.ReadKey();
        }
    }
}
```



## Hashtable

这种类型被称为键值对，和C++中差不多，主要也就是两种添加方式，一种遍历方式，还有一些常用方法，直接看一下代码：

```c#
namespace _05_Hashtable键值对集合 {
    class Program {
        static void Main(string[] args) {
            Hashtable ht = new Hashtable();
            ht.Add(1, 1);
            ht.Add(2, 2.0);
            ht.Add(3, "三");
            ht.Add("四", "四");
            ht.Remove(2);    //按照键值删除那个键值对
            ht.Add(2, 2.2);  //如果已经有了这个键值，这样会报错，不过现在上一句已经删除了
            ht[2] = 2.22;  //如果有那个键就替换值，如果没有就添加上
            if (!ht.ContainsKey(2)) {
                ht.Add(2, 2.222);
            }
            else {
                Console.WriteLine("不行，已经有过了");
            }
            foreach (var item in ht.Keys) {
                Console.WriteLine("键是{0}，对应的值是{1}",item,ht[item]);
            }
            Console.ReadKey();
        }
    }
}
```



## Path

专门用来操作路径的，命名空间IO，直接了看一下操作

```c#
namespace _06_Path类 {
    class Program {
        static void Main(string[] args) {
            string str = @"C:\Users\Gerton\source\repos\0505.Net基础班第十一天\06-Path类\Program.cs";
            //获得文件名
            Console.WriteLine(Path.GetFileName(str));
            //获得不含后缀的文件名
            Console.WriteLine(Path.GetFileNameWithoutExtension(str));
            //获得后缀
            Console.WriteLine(Path.GetExtension(str));
            //获得文件夹名
            Console.WriteLine(Path.GetDirectoryName(str));
            //获得全路径
            Console.WriteLine(Path.GetFullPath(str));
            //将两个路径组合在一起
            Console.WriteLine(Path.Combine(@"c:\a\:","b.txt"));
            Console.ReadKey();
        }
    }
}
```



## File

操作文件的，命名空间同样在IO下，这里视频少了，自己找教程学下

```c#
namespace _07_File类 {
    class Program {
        static void Main(string[] args) {
            //创建
            File.Create(@"C:\Users\Gerton\Desktop\new.txt");
            //删除
            File.Delete(@"C:\Users\Gerton\Desktop\new.txt");
            //复制
            File.Copy(@"C:\Users\Gerton\Desktop\new.txt", @"C:\Users\Gerton\Desktop\new1.txt");
        }
    }
}
```



# 第十二天

## List泛型空间

```c#
namespace _01_List泛型集合 {
    class Program {
        static void Main(string[] args) {
            List<int> lt = new List<int>();
            lt.Add(1);
            lt.Add(2);
            lt.Add(3);
            lt.AddRange(new int[] { 1, 2, 3 });
            for (int i = 0; i < lt.Count; ++i) {
                Console.WriteLine(lt[i]);
            }

            //可以转换成数组
            int[] nums = lt.ToArray();
            int[] nums2 = { 3, 2, 1 };
            List<int> lt2 = nums2.ToList();

            Console.ReadKey();
        }
    }
}
```

和原本的那个ListArray差不多，那个可以什么都放进去，这个要放一个类型，但是长度也可变，而且这个在取出来数据用的时候，不用进行类型转换，另外还有好处，就是不用进行装箱和拆箱，下面来介绍一个装箱和拆箱

* 将值类型转变成引用类型称为装箱
* 将引用类型转换成值类型称为拆箱

```c#
namespace _02_装箱和拆箱 {
    class Program {
        static void Main(string[] args) {
            int n = 10;
            object o = n; //装箱
            int nn = (int)o; //拆箱
        }
    }
}
```

下面展示一下因为装箱和拆箱所产生的时间对比

```c#
namespace _02_装箱和拆箱 {
    class Program {
        static void Main(string[] args) {
            ArrayList lt_a = new ArrayList();
            List<int> lt = new List<int>();
            Stopwatch sw = new Stopwatch();
            Stopwatch sw2 = new Stopwatch();
            sw.Start();
            for (int i = 0; i < 10000000; ++i) {
                lt_a.Add(i);//每次都是装箱
            }
            sw.Stop();

            sw2.Start();
            for (int i = 0; i < 10000000; ++i) {
                lt.Add(i);
            }
            sw2.Stop();
            Console.WriteLine(sw.Elapsed);
            Console.WriteLine(sw2.Elapsed);
            Console.ReadKey();
        }
    }
}
```

用这个程序可以看到，采用了List之后的时间要短很多，就是因为在使用ArrayList的时候，每次都是装箱。

一些装箱的思考：

```c#
namespace _02_装箱和拆箱 {
    class Program {
        static void Main(string[] args) {
            //并没有发生装箱和拆箱
            string str = "123";
            int num = Convert.ToInt32(str);
            
            //这里发生了装箱 ，IComparable是int的父类
            int num2 = 10;
            IComparable i = num2;
        }
    }
}
```

看两种类型是否了装箱或者拆箱，要看这两种类型是否存在继承关系。



## Dictionary

这个和上面Hashtable差不多，也就是刚开始就需要写清楚这个的变量类型

```c#
namespace _04_Dictionary {
    class Program {
        static void Main(string[] args) {
            Dictionary<int, string> dic = new Dictionary<int, string>();
            dic.Add(1, "张三");
            dic.Add(2, "李四");
            dic.Add(3, "王五");
            dic[1] = "新来的张三";
            foreach (var item in dic.Keys) {
                Console.WriteLine("键是{0},值是{1}", item, dic[item]);
            }
            foreach (KeyValuePair<int, string> kv in dic) {
                Console.WriteLine("键是{0},值是{1}", kv.Key, kv.Value);
            }
            Console.ReadKey();
        }
    }
}
```

这里介绍了两种遍历的方式，都测试了一下，这里无论是item还是kv都是局部变量，相当于int i 中的i是可以随便设置的。



## 多态

先看一下，如果不用多态会怎么样：

父类：

```c#
namespace _05_多态 {
    public class Person {
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }
        public Person(string name) {
            this.Name = name;
        }
        public void SayHello() {
            Console.WriteLine("你好，我是人类");
        }
    }
}
```

子类1：

```c#
namespace _05_多态 {
    public class Chinese : Person {
        public Chinese(string name) : base(name) {

        }
        public new void SayHello() {
            Console.WriteLine("你好，我叫{0},我是中国人",this.Name);
        }
    }
}
```

子类2：

```c#
namespace _05_多态 {
    public class Japanese : Person {
        public Japanese(string name) : base(name) {

        }
        public new void SayHello() {
            Console.WriteLine("你好，我叫{0}，我是日本人",this.Name);
        }
    }
}
```

主函数：

```c#
namespace _05_多态 {
    class Program {
        static void Main(string[] args) {
            Chinese chinese1 = new Chinese("孙浩天");
            Chinese chinese2 = new Chinese("刘奥琦");
            Japanese japanese1 = new Japanese("宫崎骏");
            Japanese japanese2 = new Japanese("喜多郎");
            Person[] persons = { chinese1, chinese2, japanese1, japanese2 };
            for (int i = 0; i < persons.Length; ++i) {
                persons[i].SayHello();
            }
            for (int i = 0; i < persons.Length; ++i) {
                if (persons[i] is Chinese) {
                    ((Chinese)persons[i]).SayHello();
                }
                else {
                    ((Japanese)persons[i]).SayHello();
                }
            }
            Console.ReadKey();
        }
    }
}
```

这里如果直接用persons[i]的话，只能调用父类本身的函数，所以每一次都需要转换一下，解决方法就是采用多态，多态有三种方法，依次介绍：

### 虚方法

将父类的方法标记为虚方法，在父类的方法的返回类型之前加一个virtual，这个函数可以被子类重新写一遍，子类在返回类型加override，则上面的代码会变成：

父类：

```c#
namespace _05_多态 {
    public class Person {
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }
        public Person(string name) {
            this.Name = name;
        }
        public virtual void SayHello() {
            Console.WriteLine("你好，我是人类");
        }
    }
}
```

子类1：

```c#
namespace _05_多态 {
    public class Chinese : Person {
        public Chinese(string name) : base(name) {

        }
        public override void SayHello() {
            Console.WriteLine("你好，我叫{0},我是中国人",this.Name);
        }
    }
}
```

子类2：

```c#
namespace _05_多态 {
    public class Japanese : Person {
        public Japanese(string name) : base(name) {

        }
        public override void SayHello() {
            Console.WriteLine("你好，我叫{0}，我是日本人",this.Name);
        }
    }
}
```

主函数：

```c#
namespace _05_多态 {
    class Program {
        static void Main(string[] args) {
            Chinese chinese1 = new Chinese("孙浩天");
            Chinese chinese2 = new Chinese("刘奥琦");
            Japanese japanese1 = new Japanese("宫崎骏");
            Japanese japanese2 = new Japanese("喜多郎");
            Person[] persons = { chinese1, chinese2, japanese1, japanese2 };
            for (int i = 0; i < persons.Length; ++i) {
                persons[i].SayHello();
            }
            for (int i = 0; i < persons.Length; ++i) {
                if (persons[i] is Chinese) {
                    ((Chinese)persons[i]).SayHello();
                }
                else {
                    ((Japanese)persons[i]).SayHello();
                }
            }
            Console.ReadKey();
        }
    }
}
```

这里的两个for循环里面的输出结果是一样的。



### 抽象类

这是另一种情况，如果在父类中，不知道怎么写函数怎么实现，就用抽象类，这个类无法创建对象，下面看下具体实现：

父类：

```c#
namespace _06_多态_抽象类 {
    //类需要用关键字abstratc修饰
    public abstract class Animal {
        //函数也需要用abstract修饰，并且不能有主体
        public abstract void Bark();
    }
}
```

子类1：

```c#
namespace _06_多态_抽象类 {
    public class Dog : Animal {
        public override void Bark() {
            Console.WriteLine("汪汪叫");
        }
    }
}
```

子类2：

```c#
namespace _06_多态_抽象类 {
    public class Cat : Animal {
        public override void Bark() {
            Console.WriteLine("喵喵叫"); ;
        }
    }
}
```

主函数：

```c#
namespace _06_多态_抽象类 {
    class Program {
        static void Main(string[] args) {
            Dog dog = new Dog();
            Cat cat = new Cat();
            Animal[] animals = { dog, cat };
            for (int i = 0; i < animals.Length; ++i) {
                animals[i].Bark();
            }
            Animal animal = new Animal();
            Console.ReadKey();
        }
    }
}
```

抽象类总结：

* 抽象成员必须标记为abstract，并且不能有任何实现
* 抽象成员必须在抽象类中
* 抽象类不能被实例化
* 子类继承抽象类后，必须把父类中所有抽象成员都重写(除非子类也是一个抽象类，则可以不重写)
* 抽象成员的访问修饰符不能是private
* 在抽象类中可以包含实例成员，并且抽象类的实例成员可以不被子类实现
* 抽象类是有构造函数的，虽然不能实例化
* 如果父类的抽象方法中有参数，那个继承这个抽象父类的子类在重写父类的方法的时候必须传入对应的参数，如果抽象父类的抽象方法中有返回值，那么子类在重写这个抽象方法的时候，也必须传入返回值。
* 如果父类中的方法有默认的实现，并且父类需要被实例化，这时可以考虑将父类定义为一个普通类，用虚方法来实现；如果父类中没有默认实现，父类也不需要被实例化，则可以将类定义为抽象类。



# 第十三天

## C#中的访问修饰符

访问修饰符的分类：

* public：公开的，公共的
* private：私有的，只有在当前类的内部可以访问
* protected：受保护的，只能在当前类的内部以及该类的子类中访问
* internal：只能在当前项目中访问，在同一个项目中，internal和public的权限是一样的。
* protected internal：就是protected+internal

关于访问修饰符需要注意的地方：

* 只有public和interna可以修饰类
* 可访问性不一致，子类的访问权限不能高于父类的访问权限，会暴露父类的成员。



## 简单工厂设计模式

这个就是说假如需要生产一个笔记本，但是有三种品牌，联想、戴尔、IBM，不知道要生产什么，所以只能先返回电脑的父类，当用户输入自己想要用什么品牌的时候，再说，看下代码

```c#
namespace _02_简单工厂设计模式 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入您想要的笔记本品牌：");
            string brand = Console.ReadLine();
            NoteBook nb = GetNoteBook(brand);
            nb.SayHello();
            Console.ReadKey();
            }
        //这个函数就是根据用户的输入，判断是什么品牌
        public static NoteBook GetNoteBook(string brand) {
            NoteBook nb = null;
            switch (brand) {
                case "Dell":nb = new Dell();
                    break;
                case "Lenovo":nb = new Lenovo();
                    break;
                case "IBM":nb = new IBM();
                    break;
            }
            return nb;
        }
    }
    //父类，笔记本
    public abstract class NoteBook {
        public abstract void SayHello();
    }
    //子类，戴尔笔记本
    public class Dell : NoteBook {
        public override void SayHello() {
            Console.WriteLine("你好，我是戴尔笔记本");
        }
    }
    //子类，联想笔记本
    public class Lenovo : NoteBook {
        public override void SayHello() {
            Console.WriteLine("你好，我是联想笔记本");
        }
    }
    //子类，IBM笔记本
    public class IBM : NoteBook {
        public override void SayHello() {
            Console.WriteLine("你好，我是IBM笔记本");
        }
    }
}
```



## 序列化和反序列化

* 序列化：就是将对象转换为二进制，这个类需要是可以序列化的对象，在类前面加[Serializable]
* 反序列化：就是将二进制转换为对象
* 作用：传输数据

```c#
namespace _03_序列化和反序列化 {
    class Program {
        static void Main(string[] args) {
            Person p = new Person();
            p.Name = "张三";
            p.Age = 18;
            p.Gender = '男';
            //先将这个对象写在桌面上
            using (FileStream fsWrite = new FileStream(@"C:\Users\Gerton\Desktop\p.txt", FileMode.OpenOrCreate, FileAccess.Write)) {
                //开始序列化对象
                BinaryFormatter bf = new BinaryFormatter();
                bf.Serialize(fsWrite, p);
            }
            Console.WriteLine("序列化成功");
            
            //先读取这个文件
            using (FileStream fsRead = new FileStream(@"C:\Users\Gerton\Desktop\p.txt", FileMode.OpenOrCreate, FileAccess.Read)) {
                //开始反序列化
                BinaryFormatter bf1 = new BinaryFormatter();
                bf1.Deserialize(fsRead);
            }
            Console.WriteLine(p.Name);
            Console.WriteLine(p.Age);
            Console.WriteLine(p.Gender);
            Console.WriteLine("反序列化成功");
            Console.ReadKey();
        }
    }
    [Serializable]  //指示这个对象可以序列化
    public class Person {
        private string _name;
        public string Name {
            get { return _name; }
            set { _name = value; }
        }

        private int _age;
        public int Age {
            get { return _age; }
            set { _age = value; }
        }

        private char _gender;
        public char Gender {
            get { return _gender; }
            set { _gender = value; }
        }
    }
}
```



## 部分类Partial

就是说如果一个团队中有，有多个人同时在开发，如果是一个类的话，可以同时写，语法如下：

```c#
namespace _04_部分类 {
    class Program {
        static void Main(string[] args) {
        }
    }
    public partial class Person {
        private int _age;
    }

    public partial class Person {
        public void Test() {
            _age = 10;
        }
    }
}
```

其实就是把这个类给拆分了，而且可以看到，私有的字段是可以访问的，但是不知道为啥，我不写在函数中就不行了。



## 密封类Sealed

不能够被其他类继承，但是可以继承于别的类，class前面加Sealed



## 重写父类的ToString()

C#中所有的对象都可以用ToString()，就是输出命名空间，这是因为这个方法是object类的方法，而其他的所有类都是继承的object类，所以我们也可以对这个方法进行重写。

```c#
namespace _05_重写父类的ToString__ {
    class Program {
        static void Main(string[] args) {
            Person p = new Person();
            Console.WriteLine(p.ToString());
            Console.ReadKey();
        }
    }
    public class Person {
        public override string ToString() {
            return "你好，这是我重写的ToString";
        }
    }
}
```



## 接口

这个是实现多态的第三种方法。

* 接口是一种规范，只要一个类继承了一个接口，这个类就必须实现这个接口中所有的成员
* 为了多态，接口不能被实例化，也就是说，接口不能new(不能创建对象)
* 接口中的成员不能加“访问修饰符”，接口中的成员的访问修饰符默认为public，不能修改
* 接口中只能有方法、属性、索引器、事件，不能有字段和构造函数
* 接口与接口之间可以继承，并且可以多继承
* 接口不能去继承一个类，而类可以继承接口
* 一个类可以同时继承了一个类并实现多个接口，如果一个子类同时继承了父类A，并实现了接口IA，那么语法上A必须写在IA的前面。

```c#
namespace _06_接口 {
    class Program {
        static void Main(string[] args) {
        }
    }
    public class Person {
        public void Eat() {
            Console.WriteLine("我是人类，我可以吃饭");
        }
    }
    //这是一个接口，语法如下：
    public interface IFlyable {
        //这里面的所有的方法都不能有实现，并且不能有修饰符，默认都是public
        void Fly();
        //接口不能包含属性
        //private string _name;
        //接口可以包含属性，不过不能写方法体，因为属性的本质也是方法，所以这里的属性也就是自动属性
        string Name {
            get;
            set;
        }
    }
    public class Student : Person, IFlyable {
        public void Fly() {
            Console.WriteLine("我也可以飞");
        }
    }
}
```



## 显示实现接口

为了解决方法重名的问题

```c#
namespace _07_显示实现接口 {
    class Program {
        static void Main(string[] args) {
            IFlyable fly = new Bird();
            fly.Fly();
            Bird brid = new Bird();
            brid.Fly();
            Console.ReadKey();
        }
    }
    public class Bird : IFlyable{
        public void Fly() {
            Console.WriteLine("我是鸟，我会飞");
        }
        //接口显示实现，默认访问修饰符是private，且只能是private
        void IFlyable.Fly() {
            Console.WriteLine("这个是接口的飞");
        }
    }
    public interface IFlyable {
        void Fly();
    }
}
```



# 第十四天

## MD5加密

这个是为了解决在数据库中明文存储的问题，加密一下

```c#
namespace _01_MD5加密 {
    class Program {
        static void Main(string[] args) {
            Console.WriteLine("请输入想要转换的字符串:");
            string str = Console.ReadLine();
            string newStr = GetMD5(str);
            Console.WriteLine("转换后的MD5为：{0}",newStr);
            Console.ReadKey();
        }
        public static string GetMD5(string str) {
            //创建MD5对象，因为MD5类是抽象类，不能用构造函数创建
            MD5 md5 = MD5.Create();
            //开始加密
            
            //将字符串转换成字节数组
            byte[] buffer = Encoding.Default.GetBytes(str);
            //将转换后的字符数组进行加密
            byte[] MD5Buffer = md5.ComputeHash(buffer);
            //1.将字节数组中每个元素按照指定的编码格式解析成字符串,经过测试不行
            string newStr1 = Encoding.Default.GetString(MD5Buffer);

            //2.直接就将数组ToString()，这个肯定也不行，返回是命名空间

            //3.将字节数组中的每个元素ToString()
            string newStr3 = "";
            for (int i = 0; i <　MD5Buffer.Length; ++i) {
                //ToString("x")表示按照16进制转换
                //ToString("x2")表示按照16进制同时对齐
                newStr3 += MD5Buffer[i].ToString("x2");
            }
            return newStr3;
        }
    }
}
```

这里放一下[字节数组转换成字符串](https://www.cnblogs.com/Asa-Zhu/archive/2012/11/08/2761137.html)网址，忘了的时候可以去看下。



## WinForm应用程序

WinForm应用程序是一种智能客户端技术，我们可以使用WinForm应用程序，帮助我们获得信息或者传输信息等。

### 属性

* Name：在后台获得前台的控件对象，需要使用Name属性，如果想要更改显示的话，更改Text这个属性
* Visible：指示一个控件是否可见
* Enabled：指示一个控件是否可用

### 事件

发生意见事情称为事件

* 注册事件：双击控件，注册的都是控件默认被选中的那个事件。
* 触发事件

### 窗体

在Main函数中创建的窗体对象，我们称之为这个窗体应用程序的主窗体，也就意味着，当你的主窗体关闭后，整个应用程序都关闭了。

## TextBox控件

* WordWrap：指示文本框是否可以自动换行
* ScollBars：是否显示滚动条
* PasswordChar：让文本框显示一个单一的字符，一般在输入密码的时候使用
* 事件：TextChanged当文本框中的内容发生改变的时候，触发这个事件

## Timer

在指定的时间间隔内做一个指定的事情，实现了跑马灯和闹钟两个功能，如果有不懂的话，去看下代码

