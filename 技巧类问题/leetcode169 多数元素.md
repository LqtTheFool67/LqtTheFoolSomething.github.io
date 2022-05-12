#### [169. 多数元素](https://leetcode.cn/problems/majority-element/)



#### ![image-20220512203634678](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220512203634678.png)



```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 1 ;
        int first = nums[0];
        for(int i = 1; i < nums.length;i++){
            if(nums[i] == first){
                count++;
            }else{
                count--;
                if(count == 0){
                    first = nums[i + 1];
                }
            }
            
        }
        return first;
    }
}
```



思路：

从第一个数开始count=1，遇到相同的就加1，遇到不同的就减1，减到0就重新换个数开始计数，总能找到最多的那个。