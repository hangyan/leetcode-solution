# Power of Two

> Given an integer, write a function to determine if it is a power of two.


题目翻译: 
给出一个整数，判断它是否是2的幂。

题目分析: 
2的整数次幂对应的二进制数只含有0个或者1个1，所以我们要做的就是判断输入的数的二进制表达形式里是否符合这一条件。
有一种corner case需要注意，当输入的数为负数的时候，一定不是2的幂。

时间复杂度：O(n)
空间复杂度：O(1)

代码如下:

```c++
class Solution {
public:
    bool isPowerOfTwo(int n) {
       if (n < 0) return false;
       bool hasOne = false;
       while (n > 0) {
           if (n & 1) {
               if (hasOne) {
                   return false;
               }
               else {
                   hasOne = true;
               }
           }
           n >>= 1;
       }
       return hasOne;
    }
};
```

---
似乎有一种更简单的方式,参考于：[快速判断一个数是否是2的幂次方，若是，并判断出来是多少次方！](http://blog.csdn.net/hackbuteer1/article/details/6681157)
将2的幂次方写成二进制形式后，很容易就会发现有一个特点：二进制中只有一个1，并且1后面跟了n个0； 因此问题可以转化为判断1后面是否跟了n个0就可以了。
如果将这个数减去1后会发现，仅有的那个1会变为0，而原来的那n个0会变为1；因此将原来的数与去减去1后的数字进行与运算后会发现为零。
最快速的方法：

      (number & number - 1) == 0
原因：因为2的N次方换算是二进制为10……0这样的形式(0除外)。与上自己-1的位数，这们得到结果为0。例如。8的二进制为1000；8-1=7，7的二进制为111。两者相与的结果为0。计算如下：

         1000
       & 0111
        -------
         0000



