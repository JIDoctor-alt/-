### Java输出数据的对齐方法:

>  你可以把数字转换成字符串，用 String.format("% 4d", number1); 可以补充空格
>
> 有个更好的方法用printf();这个给C中的方法差不多，很方便例如这样：
>
> System.out.printf("%-10s","abc");           //输出10列，左对齐(-号表示左对齐)
> System.out.printf("%8d",23);                   //输出8列， 右对齐



### Scanner运行超时

1. 

> 当new scanner(system.in)超时的时候，我们可以改为
>
> ```java
> Scanner scanner = new Scanner(new BufferedInputStream(System.in));
> ```

2.  java题目运行超时

> - 首先确保没有加package，类名称为Main。
>
> - 为了运行效率，请使用
>
>   [java] view plain copy
>
>   因为pat系统对scanner支持不友好且运行时间长。
>
> - BufferedReader bf=new BufferedReader(new InputStreamReader(System.in));  
>
> - 请在使用完bufferedreader之后立刻使用close()；方法关闭，否则可能会发生内存泄漏（关闭的越早越好）。
>
> - 【重要】请不要随便import没有用到的包，亲测若是导入了java.util.Scanner可是你没有用到scanner，就会返回非零。
>
> - 二、对于运行超时
>
> - 一般对于100ms时间限制的题目，基本ac不了，哪怕优化得再好。因为很多乙级题目运行时长（该死的jvm启动）在100ms上下，运气好ac的多，运气差全超时！
>
> - 200ms以上的题目，若是运行超时，那就请不要用暴力破解。
>
> - 还是超时的话，建议换语言。官方说明：选择合适的语言也是一种技巧，所以不给你java放宽时间限制！

3. 

> # 1.Scanner
>
> * scanner类在运行时候真的是巨慢无比，尤其是当要读入很多数据的时候如果用scanner，那一定能让你感受到绝望看一个，所以在读入数据时我们一般使用BufferedReader来读取数据，先来看一个对比图：
>
> * 在读入10,000,000 个整数时所需时间对比：
>
> ####            Input Method                                                       Time (sec)             
>
> ```c
> C scanf("%d",&arg)                         3.78
> Scanner.parseInt()                         29.52
> BufferedReader + inline Integer.paresInt
> BufferedReader + Reader.nextInt method     3.01
> ```
>
> 
>
> * 在读入10,000,000 个浮点数时所需时间对比：
> ####            Input Method                                                       Time (sec)             
>
> ```c
> C scanf("%lf",&arg)                         11.9
> Scanner.parseDouble()                       66.86
> BufferedReader + inline Double.parseDouble  3.06
> BufferedReader + Reader.nextDouble method   3.14
> ```
>
> * 可以看到scanner用时差不多是BufferedReader的10到20倍。
>
>   如何使用BufferedReader呢？
>
>   ```java
>   class Reader {
>       static BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
>       static StringTokenizer tokenizer = new StringTokenizer("");
>       static String nextLine() throws IOException{// 读取下一行字符串
>           return reader.readLine();
>       }
>       static String next() throws IOException {// 读取下一个字符串
>           while (!tokenizer.hasMoreTokens()) {
>               tokenizer = new StringTokenizer(reader.readLine());
>           }
>           return tokenizer.nextToken();
>       }
>   
>       static int nextInt() throws IOException {// 读取下一个int型数值
>           return Integer.parseInt(next());
>       }
>   
>       static double nextDouble() throws IOException {// 读取下一个double型数值
>           return Double.parseDouble(next());
>       }
>   }
>   //其中nextLine对应Scanner.nextLine();
>   
>   //next() 对应Scanner.next();
>   
>   //nextInt() 对应Scanner.nextInt() ;
>   
>   //nextDouble() 对应Scanner.nextDouble() ;
>   ```
>
>   2. String
>
>    ----------------------------------------------------
>
>      当我们经常要对一个字符串进行修改时，不要使用String类，因为String为静态，添加修改String会极其耗时，所以要使用StringBuilder()
>
>      ```java
>      StringBuilder s=new StringBuilder();       //建立StringBuilder的两种方式
>      StringBuilder s1=new StringBuilder("Adam");
>      s.append("hahaha"); //在字符串末尾添加字符串
>      s.insert(3,"hhh");  //在字符串中的位置插入字符串
>      s.setCharAt(1, 's'); //将字符串中指定位置字符替换
>      String s3=s.toString(); //转换为String
>      ```
>
>      



