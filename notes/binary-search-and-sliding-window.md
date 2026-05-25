二分查找与滑动窗口专题

一、二分查找三大模板
| 场景 | 循环条件 | 更新 right | 返回值 |
|------|----------|------------|--------|
| 找确定值 | `left <= right` | `mid - 1` | `mid` 或 `-1` |
| 找插入位置 | `left <= right` | `mid - 1` | `left` |
| 找边界 | `left < right` | `mid` | `left` |

基础模板
```python
left, right = 0, len(nums) - 1
while left <= right:
    mid = left + (right - left) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1
return -1

二、滑动窗口两大模板

找最长窗口
python
left = 0
for right in range(len(s)):
    加入右边元素
    while 窗口不满足条件:
        移除左边元素
        left += 1
    更新答案（每轮都更新）

找最短窗口
python
left = 0
for right in range(len(nums)):
    加入右边元素
    while 窗口满足条件:
        更新答案（满足条件时更新）
        移除左边元素
        left += 1

三、题型速查
题号	题目	核心技巧
704	二分查找	基础模板
35	搜索插入位置	找不到返回 left
278	第一个错误版本	left < right, right = mid
3	无重复字符最长子串	最长窗口模板
209	长度最小子数组	最短窗口模板
