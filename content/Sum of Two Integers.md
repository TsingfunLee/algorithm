# Sum of Two Integers
## Description
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.</br>    
Example:       </br>
Given a = 1 and b = 2, return 3.</br>
## Solution
不能使用四则运算符，所以只能用位运算来实现加法运算了。</br>
对于两个整数相加，比如462和579.</br>
不考虑进位相加：931.   </br>
只考虑进位相加：110.</br>
两部分相加：1041.这就是462和579的和。</br>
</br>
在二进制里，只有0和1两个数字，所以很容易考虑到每位所有数字相加的情况。</br>
不考虑进位相加：</br>
0+0=0，</br>
0+1=1，</br>
1+0=1，</br>
1+1=0，</br>
这是异或（^）的位运算。</br>
只考虑进位相加：</br>
0+0=0，</br>
0+1=0，</br>
1+0=0，</br>
1+1=1，（左移进了一位）</br>
这是与（&）的位运算。</br>
所以只要将加数a和b先按位异或算出和sum，再按位与然后左移一位算出进位carry，然后递归相加。</br>
代码：</br>
```c
int add(int a, int b) {
    if (b == 0) return a;
    int sum = a ^ b;
    int carry = (a & b) << 1;
    return add(sum, carry);
}
```

