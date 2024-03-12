# Assignment #2: 编程练习

Updated 0953 GMT+8 Feb 24, 2024

2024 spring, Complied by 彭博翔 物理学院

**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。

**编程环境**

操作系统：windows 11 22621.3155

Python编程环境：Spyder IDE 5.2.2

## 1. 题目

### 27653: Fraction类

http://cs101.openjudge.cn/practice/27653/



思路：暂时没有很好的思路



##### 代码

```python

```



代码运行截图 ==（至少包含有"Accepted"）==





### 04110: 圣诞老人的礼物-Santa Clau’s Gifts

greedy/dp, http://cs101.openjudge.cn/practice/04110

思路：先算平均值，根据平均值排序，依次装入背包。

##### 代码

```python
n,w = [int(a) for a in input().split( )]
li = []
for i in range(n):
    a,b = [int(x) for x in input().split()]
    pj = a/b
    am = [pj,a,b]
    li.append(am)
li.sort()
ans = 0
for i in range(n):
    if w >= li[-1-i][-1]:
        ans += li[-1-i][0]*li[-1-i][-1]
        w -= li[-1-i][-1]
    else:
        ans += li[-1-i][0]*w
        w = 0
print(ans)
```

代码运行截图 ==（至少包含有"Accepted"）==

![image-20240303172927287](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240303172927287.png)

### 18182: 打怪兽

implementation/sortings/data structures, http://cs101.openjudge.cn/practice/18182/

思路：没什么好的思路，所以就根据题目描述遍历多次，所以代码很长。

##### 代码

```python
nC = int(input())
for i in range(nC):
    n,m,b = [int(a) for a in input().split()]
    li = []
    time = []
    for j in range(n):
        t,h = [int(a) for a in input().split()]
        su = [t,h]
        li.append(su)
        time.append(t)
    time.sort()
    se = set(time)
    se = sorted(se)
    li.sort()
    dp = []
    di = {}
    for key in time:
        di[key] = di.get(key,0) + 1
    s = 0
    for j in se:
        ti = di[j]
        s += ti
        hurt = 0
        if ti <= m:
            for x in range(s-ti,s):
                hurt += li[x][1]
            dp.append([j,hurt])
        else:
            for x in range(s-m,s):
                hurt += li[x][1]
            dp.append([j,hurt])
    for j in range(len(dp)):
        if b > dp[j][1]:
            b -= dp[j][1]
        else:
            b = 0
            print(dp[j][0])
            break
    if b > 0:
        print('alive')
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240303182702647](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240303182702647.png)

### 230B. T-primes

binary search/implementation/math/number theory, 1300, http://codeforces.com/problemset/problem/230/B

思路：一开始的思路是利用上次哥德巴赫猜想的判断质数代码，然后将现在的数值开方，判断是否为质数，但是很遗憾超时了。后面换用更快速的判断方式，最后成功AC

##### 代码

```python
n = 1000000
li = [1]*n
s = set()
for i in range(2,n):
    if li[i]==1:
        s.add(i*i)
        for j in range(i*i,n,i):
            li[j]=0
m = int(input())
ans = list(map(int,input().split()))
for i in range(m):
    if ans[i] in s:
        print("YES")
    else:
        print("NO")
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240305155836847](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240305155836847.png)

### 1364A. XXXXX

brute force/data structures/number theory/two pointers, 1200, https://codeforces.com/problemset/problem/1364/A

思路：

##### 代码

```python
n = int(input())
for i in range(n):
    a,b = [int(x) for x in input().split()]
    ans = -1
    A = list(map(lambda x: int(x) % b, input().split()))
    if sum(A) % b != 0:
        print(a)
        continue
    for j in range(a//2+1):
        if A[j] != 0 or A[-j-1] != 0:
            ans = a-j-1
            break
    print(ans)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240312122318323](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240312122318323.png)

### 18176: 2050年成绩计算

http://cs101.openjudge.cn/practice/18176/

思路：思路与T-primes类似，具体改动一些。

##### 代码

```python
n = 10000
li = [1]*n
s = set()
for i in range(2,n):
    if li[i]==1:
        s.add(i*i)
        for j in range(i*i,n,i):
            li[j]=0
m,n = [int(a) for a in input().split()]
for i in range(m):
    grade = list(int(a) for a in input().split())
    ans = []
    for j in grade:
        if j in s:
            ans.append(j)
    if sum(ans) == 0:
        print(0)
    else:
        an = sum(ans)/len(grade)
        print("%.2f" % an)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240305161331304](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240305161331304.png)

## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“2024spring每日选做”、CF、LeetCode、洛谷等网站题目。==

本次作业有部分以前计概的时候做过，AC后看以前的代码，发现思路有些不同，现在的代码没有以前简洁（考虑到以前是长期编程的结果，更熟练也是合理的），但是现在往往能一遍就AC，以前可能还会WA。总之，希望经过这一学期的练习，能更快，更简洁，更精确吧。

