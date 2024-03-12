# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by 彭博翔 物理学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：windows 11 22621.3155

Python编程环境：Spyder IDE 5.2.2

## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/

思路：

##### 代码

```python
k = int(input())
li = list(int(a) for a in input().split())
dp = []
for i in range(k):
    dp.append([0,li[-i-1]])
for i in range(1,k):
    dp[0][0] = 1
    an = [1]
    for j in range(i):
        if dp[j][1] <= dp[i][1]:
            an.append(dp[j][0]+1)
    dp[i][0] = max(an)
dp.sort()
print(dp[-1][0])
```

代码运行截图 ==（至少包含有"Accepted"）==

![image-20240310140332553](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240310140332553.png)

**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147

思路：

##### 代码

```python
def moveOne(numDisk : int, init : str, desti : str):
    print("{}:{}->{}".format(numDisk, init, desti))

def move(numDisks : int, init : str, temp : str, desti : str):
    if numDisks == 1:
        moveOne(1, init, desti)
    else: 
        move(numDisks-1, init, desti, temp) 
        moveOne(numDisks, init, desti) 
        move(numDisks-1, temp, init, desti)

n, a, b, c = input().split()
move(int(n), a, b, c)
```

代码运行截图 ==（至少包含有"Accepted"）==

![image-20240311141002060](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240311141002060.png)

**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253

思路：

##### 代码

```python
while True:
    n,p,m = [int(a) for a in input().split()]
    if n == p == m == 0:
        break
    li = []
    for i in range(n):
        li.append(i+1)
    for i in range(p-1):
        a = li.pop(0)
        li.append(a)
    ans = []
    for i in range(1,m*n+1):
        a = li.pop(0)
        li.append(a)
        if i%m == 0:
            b = li.pop(-1)
            ans.append(a)
    print(','.join(map(str,ans)))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240310221531121](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240310221531121.png)

**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554

思路：

##### 代码

```python
n = int(input())
li = list(int(a) for a in input().split())
dp = []
for i in range(len(li)):
    dp.append([li[i],i+1])
dp.sort()
ans = []
su = 0
for i in range(n):
    ans.append(dp[i][1])
    su += dp[-i-1][0]*(i)
an = su/n
print(' '.join(map(str,ans)))
print("%.2f" % an)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240310212726093](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240310212726093.png)

**19963:买学区房**

http://cs101.openjudge.cn/practice/19963

思路：

##### 代码

```python
n = int(input())
pairs = [i[1:-1] for i in input().split()]
dis = [ sum(map(int,i.split(','))) for i in pairs]
pri = list(int(a) for a in input().split())
dp = []
for i in range(n):
    dp.append([dis[i]/pri[i],i+1,dis[i],pri[i]])
dp.sort()
pri.sort()
if n%2==1:
    mid = dp[n//2][0]
else:
    mid = (dp[(n//2)-1][0]+dp[n//2][0])/2
if n%2==1:
    mid_pri = pri[n//2]
else:
    mid_pri = (pri[(n//2)-1]+pri[n//2])/2
ans = []
for i in range(n):
    if dp[i][0] > mid and dp[i][3] < mid_pri:
        ans.append(dp[i][1])
print(len(ans))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240311144339622](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240311144339622.png)

**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300

思路：

##### 代码

```python
from collections import defaultdict

n = int(input())
di = defaultdict(list)
for i in range(n):
    name,ans = input().split('-')
    if ans[-1] == 'M':
        di[name].append((float(ans[0:-1])/1000,ans))
    else:
        di[name].append((float(ans[0:-1]),ans))
dic = sorted(di)
for i in dic:
    lis = []
    di[i].sort()
    for j in range(len(di[i])):
        lis.append(di[i][j][1])
    print(i + ": " + ', '.join(lis))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240311135918409](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240311135918409.png)

## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“2024spring每日选做”、CF、LeetCode、洛谷等网站题目。==

月考的时候因个人原因，没有参加，后面找时间完成的这次作业。在月考规定时间内，只能AC4，做题的速度还是比较慢。其他课程学习任务也比较重，而且语法也还没有恢复到以前学计概的水平，每日选做还没有开始做，计划在清明节过后开始作每日选做。



