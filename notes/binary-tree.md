二叉树专题

一、遍历方式
| 遍历方式 | 顺序 | 口诀 | 数据结构 |
|----------|------|------|----------|
| 前序遍历 | 根 → 左 → 右 | 根左右 | 栈（Stack） |
| 中序遍历 | 左 → 根 → 右 | 左根右 | 栈（Stack） |
| 后序遍历 | 左 → 右 → 根 | 左右根 | 栈（Stack） |
| 层序遍历 | 一层一层 | BFS | 队列（Queue） |

二、DFS 递归模板（前序）
```python
def dfs(node):
    if not node:
        return
    # 处理当前节点（前序位置）
    dfs(node.left)
    dfs(node.right)

三、BFS 层序遍历模板
from collections import deque

queue = deque([root])
while queue:
    level_size = len(queue)
    for _ in range(level_size):
        node = queue.popleft()
        # 处理当前节点
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)

四、核心题型速查
题号	题目	核心技巧
102	层序遍历	BFS 母题
104	最大深度	max(左,右) + 1
111	最小深度	分四种情况（空子树处理）
110	平衡二叉树	abs(左-右) > 1，返回 -1
543	二叉树的直径	left + right 拐弯
124	最大路径和	max(0, left) 过滤负数
101	对称二叉树	镜像成对比较（BFS/DFS）

五、DFS 深度题通用模板
def dfs(node):
    if not node:
        return 0
    left = dfs(node.left)
    right = dfs(node.right)
    # 根据题目处理 left 和 right
    return max(left, right) + 1
