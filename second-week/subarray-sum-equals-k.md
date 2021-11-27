## subarray-sum-equals-k



#### Description

给你一个整数数组 `nums` 和一个整数 `k` ，请你统计并返回该数组中和为 `k` 的连续子数组的个数。



#### Example

**Example 1：**

```
输入：nums = [1,1,1], k = 2
输出：2
```

**Example 2：**

```
输入：nums = [1,2,3], k = 3
输出：2
```



#### Solution

```js
var subarraySum = function(nums, k) {
    let mp = new Map()
    mp.set(0, 1)
    let count = 0, pre = 0
    for (const x of nums) {
        pre += x
        if (mp.has(pre - k)) {
            count += mp.get(pre - k)
        }
        if (mp.has(pre)) {
            mp.set(pre, mp.get(pre) + 1)
        } else {
            mp.set(pre, 1)
        }
    }
    return count
};
```



#### Result

![image-20211127171155285](image/image-20211127171155285.png)