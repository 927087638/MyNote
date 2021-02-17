# Java

> - **Project：**项目，是最大的范围，可以被认为是Java程序的最上层。一个项目可以包含若干个Package。不同Project之间，基本上没有任何关系。
> - **Package：**包，可以包含若干个Class。包的引入，是为了对各个类进行分层管理，在同一个包与不同的包之中，权限会有所不同。同时，这样也可以使程序的结构清晰，有点像文件目录的感觉。
> - **Class：**类文件。同一个类中，没有访问权限的限制。但是，请注意一点，<u>每一个.class文件中最多只能有一个public类，并且类名称必须和文件名称一致。</u>

---

## 基本程序
### 数字变量转换

![image-20210123191451324](pic\Capture1.PNG)

### String 

> - 共享——便于内存管理、不能改单个字符

​	API

```java
int length():
char charAt(int index):

int indexOf(int ch, int fromIndex=0)     // 从fromIndex指定位置开始，获取ch在字符串中出现的位置。
int indexOf(String str, int fromIndex)   // 从fromIndex指定位置开始，获取str在字符串中出现的位置。
int lastIndexOf(int ch)

int compareTo(string);                        //字典序

boolean startsWith(str);
boolean endsWith(str);
boolean contains(str)
boolean isEmpty()

boolean equals(str);                            //区别于 ==
boolean equalsIgnoreCase();

String(char[])
String(char[],offset,count)                   //将字符数组中的一部分转成字符串。

String substring(begin);
String substring(begin,end);

String toUpperCase();
String toLowerCase();

String trim();                                      //将字符串两端的多个空格去除。
```

```java
StringBuilder //拼接更加高效
```

#### StringBuilder——可变的字符串

<p align="right"> <font size=5>用于字符串<b>频繁拼接</b></font></p>

```java
StringBuilder sb1;
StringBuilder sb2=sb1.append("123");
//此时sb1 sb2 内容、地址都相同

sb.reverse() 
```



### ArrayList

```java
ArrayList<String> array = new ArrayList<string>();
array.add("123");	//append
array.add(0,"456");	//插入到对应下标

array.remove("123");
array.remove((int)index);	//若整形数组，只可下标删除

array.get(index);
```




### IO

####  字符

```java
import java.util.*;

Scanner in = new Scanner(System.in);
String word = in.nextLine();
String sentance = in.next();
int i = in.nextInt();

boolean in.hasNext();
boolean in.hasNextInt();
```

```java
System.out.printf("%d",9418);
```

#### 文件

```java
Scanner in = new Scanner(new File(path));    //文件读取
PrintWriter out = new PrintWriter(path);     //文件写入

```

