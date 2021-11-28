# DFS-深度优先遍历
  - 括号生成
  - N皇后问题
  - 字符串的排列
  - 数字字符串转化成IP地址
  - 集合的所有子集(一)
  - 加起来和为目标值的组合(二)
  - 岛屿数量
## 总结规律. 
def main(): <br>
初始化结果的list或者int. <br>
如果需要return路径/可能情况之类的，初始化sub_list记录. <br>
dfs(初始index，空的list，sub_list). <br>
return 结果.  <br>
def dfs(): <br>
if index超过 || 已经访问过: <br>
  return <br>
for (各种可能的路径): <br>
if 不满足条件： <br>
continue <br>
走一步 <br>
self.dfs(index+1,...) <br>
回退 <br>
## 可能错误情况
1.总是return 空的结果，或者数量是0
return的值在dfs里面没有作为参数传入
