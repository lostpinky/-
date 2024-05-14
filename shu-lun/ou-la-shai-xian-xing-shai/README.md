# 欧拉筛（线性筛）

```python
# 欧拉筛
M = 10**6 + 1
primes = []
is_prime = [True] * M
for i in range(2, M):
    if is_prime[i]:
        primes.append(i)
    for p in primes:
        # 此处注意判断边界，否则若i是质数会导致遍历整个primes列表
        if p * i >= M:
            break
        # p <= i的最小质因子，否则p*i的最小质因子不为p，无法保证合数仅被标记一次（也即线性）
        is_prime[p * i] = False
        if i % p == 0:
            break
```

