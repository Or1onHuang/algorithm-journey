回溯算法专题
一、核心框架

回溯 = 决策树的深度优先遍历（DFS）

```python
def backtrack(参数):
    if 终止条件:
        保存结果
        return
    
    for i in range(起点, 终点):
        if 剪枝条件:
            continue
        做选择
        backtrack(新参数)
        撤销选择
二、三问识别法

拿到题目先问自己：

“所有可能的...” → 识别为回溯
顺序重要吗？不重要 → 子集/组合模板；重要 → 排列模板
可以重复选吗？可以 → backtrack(i)；不可以 → backtrack(i+1)
三、三大题型模板

1. 子集型（78 / 90）

特点：每个节点都保存，start 防回头
去重：i > start and nums[i] == nums[i-1]
2. 排列型（46 / 47）

特点：必须选完才保存，used 防重复
去重：nums[i] == nums[i-1] and not used[i-1]
3. 组合型（39 / 40 / 77）

特点：有目标和，终止条件是 remaining == 0
可重复选：backtrack(i)；不可重复：backtrack(i+1)
四、去重条件速查

题型	去重条件	含义
子集去重	i > start and nums[i] == nums[i-1]	同层跳过
排列去重	nums[i] == nums[i-1] and not used[i-1]	同一轮跳过
组合去重	i > start and candidates[i] == candidates[i-1]	和子集一样
