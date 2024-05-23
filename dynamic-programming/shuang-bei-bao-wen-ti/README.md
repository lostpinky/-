# 双背包问题

```python
# 双背包问题的板子
# dp[i][j][k]表示第i件物品 第一个背包容量j 第二个背包容量k 所能得到的最大价值
# 三种状态转移 1、不装  2、装第一个背包  3、装第二个背包
# 记得01背包状态压缩 第一维可以从后向前 不需要
 
 
v = list(map(int, input().split()))
# v = [6, 5, 5, 4, 3]
n = len(v)
v = [0] + v
 
# 每个背包物品价值，这里其实都是1
# w1=list(map(int,input().split()))
# w1 = [1, 1, 1, 1, 1]
# w1=[0]+w1
 
# w2=list(map(int,input().split()))
# w2 = [1, 1, 1, 1, 1]
# w2=[0]+w2
 
# 背包容量
c1, c2 = map(int, input().split())
# c1 = 8
# c2 = 9
 
# 背包容量
dp = [[0 for i in range(100)] for j in range(100)]
 
ans = 0
 
for i in range(1, n + 1):
    for j in range(c1, -1, -1):
        for k in range(c2, -1, -1):
            x1 = 0
            x2 = 0
            if j >= v[i]:
                # x1=max(dp[j][k],dp[j-v[i]][k]+w1[i])
                x1 = max(dp[j][k], dp[j - v[i]][k] + 1)
            if k >= v[i]:
                # x2 = max(dp[j][k], dp[j][k-v[i]]+w2[i])
                x2 = max(dp[j][k], dp[j][k - v[i]] + 1)
            dp[j][k] = max(dp[j][k], x1, x2)
            ans = max(ans, dp[j][k])
 
# print(dp)
print(ans)
```
