寻找重复数

快慢指针方法，与环形链表相似。

将i→nums[i] 相连。由于存在的重复的数字所以会成环，与环形链表相似，使用快慢指针的方法解决问题

环形链表找节点推理过程：
假设环长为 LL，从起点到环的入口的步数是 aa，从环的入口继续走 bb 步到达相遇位置，从相遇位置继续走 cc 步回到环的入口，则有 b+c=Lb+c=L，其中 LL、aa、bb、cc 都是正整数。根据上述定义，慢指针走了 a+ba+b 步，快指针走了 2(a+b)2(a+b) 步。从另一个角度考虑，在相遇位置，快指针比慢指针多走了若干圈，因此快指针走的步数还可以表示成 a+b+kLa+b+kL，其中 kk 表示快指针在环上走的圈数。联立等式，可以得到

```2(a+b)=a+b+kL```

```2(a+b)=a+b+kL```

解得 a=kL-ba=kL−b，整理可得

```a=(k-1)L+(L-b)=(k-1)L+c```

```a=(k−1)L+(L−b)=(k−1)L+c```

```

class Solution {

public:

    int findDuplicate(vector<int>& nums) {
        int slow = 0, fast = 0;
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);
        slow = 0;
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
}; 
```
