## 003:打印ASCII码

- [查看](http://cxsjsxmooc.openjudge.cn/2019t1fallall/003/)
- [提交](http://cxsjsxmooc.openjudge.cn/2019t1fallall/003/submit/)
- [统计](http://cxsjsxmooc.openjudge.cn/2019t1fallall/003/statistics/)
- [提问](http://cxsjsxmooc.openjudge.cn/2019t1fallall/clarify/003/)

- 总时间限制: 

  1000ms

- 内存限制: 

  65536kB

- 描述

  输入一个除空格以外的可见字符（保证在函数scanf中可使用格式说明符%c读入），输出其ASCII码。 

- 输入

  一个除空格以外的可见字符。

- 输出

  一个十进制整数，即该字符的ASCII码。

- 样例输入

  `A`

- 样例输出

  `65`

```java
package October21th;

import java.util.Scanner;

public class Test3 {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		String s = in.next();
		char cr = s.charAt(0);
		System.out.println(cr-0);
//		System.out.printf("%d",cr);
	}
}
```

