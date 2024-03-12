# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by 彭博翔 物理学院



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：windows 11 22621.3155

Python编程环境：Spyder IDE 5.2.2

## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/

思路：先构造一个泰波拿契数列，根据输入调用数列即可

##### 代码

```python
n = int(input())
T = [0,1,1]
for i in range(2,30):
    a = 0
    a = T[i-2]+T[i-1]+T[i]
    T.append(a)
print(T[n])
```

代码运行截图 ==（至少包含有"Accepted"）==

![image-20240221142444805](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240221142444805.png)

### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A

思路：将输入单词和目标单词按顺序逐个比较，若字母对应，则比较下一个字母。

##### 代码

```python
word = input()
need = "hello"
c = 0
for i in word:
    if i == need[c]:
        c += 1
    if c == 5:
        break
if c == 5:
    print("YES")
else:
    print("NO")
```

代码运行截图 ==（至少包含有"Accepted"）==

![image-20240227154401280](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240227154401280.png)

### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A

思路：先将单词小写，然后依次判断字母，如果非韵母就加到最后的答案字符串中。

##### 代码

```python
word = input()
word = word.lower()
ans = ""
li = ['a','o','e','i','u','y']
for i in range(len(word)):
    if word[i] in li:
        ans = ans
    else:
        ans = ans + "." + str(word[i])
print(ans)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227161253384](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240227161253384.png)

### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/

思路：先找出10000以内的所有质数，然后依次判断n是否可以被分成两个质数。（存在的问题，耗时较长）

##### 代码

```python
li = [2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97]
lis = li
for i in range(100,10000):
    c = 0
    for j in li:
        if i%j==0:
            c = 1
    if c == 0:
        lis.append(i)
n = int(input())
for i in range(n):
    if i in lis and n-i in lis:
        print(i,n-i)
        break
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240228140210275](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240228140210275.png)

### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/

思路：将多项式分成单项式，对于每个单项式，如果系数不为0，提取其指数，比较指数大小，输出指数最大的一项。

##### 代码

```python
li = [a for a in input().split("+")]
a = []
for i in range(len(li)):
    b,c = [a for a in li[i].split("^")]
    if b[0] != str(0):
        a.append(int(c))
a.sort()
print("n^" + str(a[-1]))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227165410370](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240227165410370.png)

### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/

思路：先将输入构成一个列表，再转为集合（去重），对集合的每个元素建立字典，利用列表构成字典的键值。找出字典键最大值，放入新列表，排序，最后按顺序输出。

##### 代码

```python
li = list(map(int,input().split( )))
li.sort()
se = set(li)
s = sorted(se)
di = dict.fromkeys(s,0)
for i in range(len(li)):
    a = li[i]
    di[a] += 1
ans = []
max_li = max(di.values())
for i in s:
    if di[i] == max_li:
        x = str(i)
        ans.append(x)
an = ' '
print(an.join(ans))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240228133502164](C:/Users/彭博翔/AppData/Roaming/Typora/typora-user-images/image-20240228133502164.png)

## 2. 学习总结和收获

上次学习python是大一上的计算概论，当时也是选的闫老师的班，最后学到了不少东西，大一下因为课程方面比较忙碌，没有选择数算，这次大二下知道闫老师开了数算的班后，马上决定这学期学数算。虽然一年多没写过代码了，很多语法都忘记了，但是现在重新开始捡起来的时候，我又找回了当时写代码做题的快乐，希望自己经过这一学期的学习，能够有所收获。



