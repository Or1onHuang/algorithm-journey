双指针专题

一、三大形态
| 类型 | 指针移动方向 | 代表题目 | 核心思想 |
|------|-------------|----------|----------|
| 快慢指针 | 同向移动 | 26, 27, 283 | slow 占位，fast 探路 |
| 左右指针 | 相向移动 | 977, 344, 125 | 两边往中间夹 |
| 逆向指针 | 从后往前 | 88 | 避免覆盖，从后往前填 |

二、快慢指针模板
```python
slow = 0  # 或 1
for fast in range(len(nums)):
    if 条件满足:
        nums[slow] = nums[fast]  # 或 交换
        slow += 1
return slow
题型与条件

题目	条件	slow 初始值	操作
26. 删除重复项	nums[fast] != nums[fast-1]	1	覆盖
27. 移除元素	nums[fast] != val	0	覆盖
283. 移动零	nums[fast] != 0	0	交换

三、左右指针模板
python
left, right = 0, len(nums) - 1
while left <= right:  # 或 left < right
    if 条件:
        left += 1
    else:
        right -= 1

四、逆向指针模板（88. 合并有序数组）
python
p1, p2 = m - 1, n - 1
p = m + n - 1
while p2 >= 0:
    if p1 >= 0 and nums1[p1] > nums2[p2]:
        nums1[p] = nums1[p1]
        p1 -= 1
    else:
        nums1[p] = nums2[p2]
        p2 -= 1
    p -= 1
