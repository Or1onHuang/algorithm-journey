动态规划专题
一、DP 三板斧
任何 DP 题都先问自己三个问题：
1. **定义状态**：`dp[i]` 或 `dp[i][j]` 表示什么？
2. **找转移方程**：怎么从前面推出后面？
3. **初始化边界**：前几个值怎么确定？

二、一维 DP 题型
| 题号 | 题目 | 转移方程 | 核心技巧 |
|------|------|----------|----------|
| 70 | 爬楼梯 | `cur = prev1 + prev2` | 斐波那契 |
| 746 | 最小花费爬楼梯 | `cur = min(prev1+cost[i-1], prev2+cost[i-2])` | 带权选择 |
| 198 | 打家劫舍 | `cur = max(prev1, prev2+nums[i])` | 选/不选 |
| 53 | 最大子数组和 | `cur = max(cur+nums[i], nums[i])` | 接/不接 |
| 213 | 打家劫舍 II | 同上 × 2 | 环形拆直线 |

空间优化口诀
```python
cur = 计算(prev1, prev2)
prev2 = prev1
prev1 = cur

三、二维 DP 题型
题号	题目	转移方程	核心
62	不同路径	dp[i][j] = dp[i-1][j] + dp[i][j-1]	路径数
63	不同路径 II	同上，障碍物 = 0	障碍物处理
64	最小路径和	dp[i][j] = min(上,左) + grid[i][j]	最小花费
二维 DP 固定骨架

python
m, n = len(grid), len(grid[0])
dp = [[0] * n for _ in range(m)]
dp[0][0] = 起点值
# 初始化第一行和第一列
for i in range(1, m):
    for j in range(1, n):
        dp[i][j] = 合并(dp[i-1][j], dp[i][j-1])
return dp[m-1][n-1]

四、题型识别速查
关键词	题型	模板
“有多少种方法”	计数 DP	加法
“最小/最大花费”	最优 DP	min / max
“选或不选”	打家劫舍	max(不选, 选)
网格 + 路径	二维 DP	dp[i-1][j] + dp[i][j-1]
