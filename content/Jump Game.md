# Jump Game
## Description
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:
A = `[2,3,1,1,4]`, return `true`.

A = `[3,2,1,0,4]`, return `false`.
## Solution
这题想了蛮久的，都没想出正确的解决方法。原来一直都在想从左往右跳要怎么跳，其实倒过来，从右往左思路就很简单了。</br>
举个栗子：</br>
数组：</br>
index `0 1 2 3 4 5 6 7 8 9`</br>
nums `4 5 5 0 2 3 1 2 0 0`</br>
先从最后一位开始，假设最后一位可以到达。</br>
然后从倒数第二位开始判断，这一位能不能到达最后一位。</br>
倒数第二位是0，无法跳到最后一位，再往前看前一位，前一位是2，刚好能跳到最后一位，那么只要之前的位置能跳到2这个位置，那就能到达最后一位。</br>
再看看前面有没有位置能到达2这个位置。2的前一位是1，显然可以跳到2。再看1前面有没有可以跳到1的，显然，3也是可以的。就这样以此类推。</br>
这种算法叫做贪心法。</br>
代码：
```
public class Solution {
    public boolean canJump(int[] nums) {
        int lastPos = nums.length - 1;
        for (int i = nums.length - 1; i >= 0; i--) {
            if (i + nums[i] >= lastPos) {
                lastPos = i;
            }
        }
        return lastPos == 0;
    }
}
```
