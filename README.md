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

