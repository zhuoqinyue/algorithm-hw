## degree-of-an-array



#### Description

给定一个非空且只包含非负数的整数数组 nums，数组的度的定义是指数组里任一元素出现频数的最大值。

你的任务是在 nums 中找到与 nums 拥有相同大小的度的最短连续子数组，返回其长度。



#### Example

```
输入：[1, 2, 2, 3, 1]
输出：2
解释：
输入数组的度是2，因为元素1和2的出现频数最大，均为2.
连续子数组里面拥有相同度的有如下所示:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
```



#### Solution

```js
var findShortestSubArray = function (nums) {
  //遍历存储次数和区间
  let map = {}
  for (let i = 0; i < nums.length; i++) {
    let value = nums[i]
    if (!map[value]) {
      map[value] = [1, i, i]
    } else {
      map[value][0]++
      map[value][2] = i
    }
  }

  //找到度
  let max = 0
  for (let key in map) {
    max = Math.max(max, map[key][0])
  }

  //根据度找到最小区间
  let min = nums.length
  for (let key in map) {
    if (max === map[key][0]) {
      min = Math.min(min, map[key][2] - map[key][1] + 1)
    }
  }

  return min
};
```



#### Result

![image-20211127170757607](image/image-20211127170757607.png)