The 3rd Universal Cup 做题记录

[https://www.cnblogs.com/yhddd/p/18415768](https://www.cnblogs.com/yhddd/p/18415768)

[Stage 0: Trial Contest](https://qoj.ac/contest/1695) ADFGHIJM

[Stage 1: St. Petersburg](https://qoj.ac/contest/1696) ACDGHJKNO

[Stage 4: Hongō](https://qoj.ac/contest/1738) BCDEKLNO

[Stage 5: Moscow](https://qoj.ac/contest/1741) ABEFGIKM

[Stage 6: Osijek](https://qoj.ac/contest/1762) ABCDHIJKL

[Stage 7: Warsaw](https://qoj.ac/contest/1774) ABEGKL

[Stage 8: Cangqian](https://qoj.ac/contest/1780) BCDEFHIJLM

[Stage 9: Xi'an](https://qoj.ac/contest/1784) AEFGHIJN

## [The 3rd Universal Cup. Stage 0: Trial Contest](https://qoj.ac/contest/1695)

### [A. Arrested Development](https://qoj.ac/contest/1695/problem/8768)

$O(n^2V)$ dp 可过。

### [D. Dihedral Group](https://qoj.ac/contest/1695/problem/8771)

一定是正序或倒序的连续区间。

### [F. Magic Bean](https://qoj.ac/contest/1695/problem/8773)

可以只交换一个环的 $4$ 号和另一个环的 $1$ 号。

### [G. Manhattan Walk](https://qoj.ac/contest/1695/problem/8774)

每个位置独立。设 $dp_{i,j}$ 为 $(i,j)$ 去到终点的期望，$dp_{i+1,j},dp_{i,j+1}$ 分别为 $a,b$，$a<b$。如果 $a+p\le b$ 一定走 $a$，否则按等待时间划分走 $a$ 还是 $b$。

### [H. MountainCraft](https://qoj.ac/contest/1695/problem/8775)

查询区间并。线段树维护区间最小值和区间最小值个数。

### [I. Not Another Constructive!](https://qoj.ac/contest/1695/problem/8776)

在 ```A``` 处计算前缀 ```N``` 和后缀 ```C``` 的乘积。设 $dp_{i,j,k,num}$ 为前 $i$ 个，前缀有 $j$ 个，后缀有 $k$ 个，能否有 $num$ 个子序列。bitset 优化。

### [J. Passport Stamps](https://qoj.ac/contest/1695/problem/8777)

模拟。

### [M. Training, Round 2](https://qoj.ac/contest/1695/problem/8780)

记录前 $i$ 个题能否达到 $(j,k)$。每个 $(j,k)$ 只会更新一次。set 维护。

## [The 3rd Universal Cup. Stage 1: St. Petersburg](https://qoj.ac/contest/1696)

### [A. Element-Wise Comparison](https://qoj.ac/contest/1696/problem/8781)

bitset 维护 $f_{i,j}=a_i<a_j$。每 $m$ 个点划一个段，统计跨过段的答案，维护一段的后缀 or。

### [C. Cherry Picking](https://qoj.ac/contest/1696/problem/8783)

从大往小加，线段树维护区间前缀后缀和最大连续 $1$。

### [D. Dwarfs' Bedtime](https://qoj.ac/contest/1696/problem/8784)

在 $0$ 时刻先每个问一次，然后每隔 $49,48,\dotsb ,1$ 问一次，问到状态翻转就挂到 $12$ 小时后连续的问。

### [G. Unusual Case](https://qoj.ac/contest/1696/problem/8787)

随机一个点开始找，当前找到 $a_1,\dotsb,a_k$，如果找不到新的出边，那么 $a_k$ 连向 $a_p$，将路径改为 $a_1\to\dotsb\to a_{p-1}\to a_p\to a_k\to a_{k-1}\dotsb\to a_{p+1}$。据题解说是 $O(n)$ 的。

### [H. Page on vdome.com](https://qoj.ac/contest/1696/problem/8788)

答案为 $\min(n+1,10)$。

### [J. First Billion](https://qoj.ac/contest/1696/problem/8790)

对 $a_i\bmod B$ 做 bitset 背包，还原方案时如果既可以选也可以不选，就随一个。取 $B=2.5\times 10^6$。

也可以分为若干块，块内折半，块间选绝对值前 $k$ 小合并。

### [K. Tasks and Bugs](https://qoj.ac/contest/1696/problem/8791)

模拟。

### [N. (Un)labeled graphs](https://qoj.ac/contest/1696/problem/8794)

$\log n$ 个点维护每个点的编号，把 $\log n$ 个点连成一条链。剩下 $3$ 个点。取 $a$ 为度数最大的点，$b$ 标记所有的 $n$ 个点，$c$ 是唯一不连 $a$ 的点，标记 $b$ 和 $\log n$ 个点的链头。

### [O. Mysterious Sequence](https://qoj.ac/contest/1696/problem/8795)

模拟。

## [The 3rd Universal Cup. Stage 4: Hongō](https://qoj.ac/contest/1738)

### [B. Black or White 2](https://qoj.ac/contest/1738/problem/9114)

令 $k=\min(k,nm-k)$，$n>m$。第 $1$ 行隔一个填一个，之后插空一次填 $(i,j)$ 和 $(i-1,j)$。多出来的填 $(n,m)$。

### [C. Contour Multiplication](https://qoj.ac/contest/1738/problem/9115)

$dp_{i,s}$ 为与 $popcount(s\oplus t)=i$ 的所有 $t$ 的共同系数。依次枚举 $j$ 将 $dp_{i,s}\to dp_{i-1}{s\oplus 2^j}$。

### [D. DRD String](https://qoj.ac/contest/1738/problem/9116)

设 $dp_i$ 为长为 $i$ 且不存在 $s[1,j]=s[i-j+1,i],j<i-j+1$ 的方案数。前缀和转移。

### [E. Equally Dividing](https://qoj.ac/contest/1738/problem/9117)

只要 $sum\bmod n=0$ 就有解。若 $m$ 为偶，每列交替升序降序；否则 $n$ 为奇，可以构造前 $3$ 列填 $[1,3n]$。

### [K. Kth Sum](https://qoj.ac/contest/1738/problem/9123)

升序排序，二分答案 $x$。对于每个 $i$ 可以 $O(n)$ 计算 $(i,j,k)$ 的答案。设阈值 $B$，前 $B$ 个的贡献 $O(nB)$ 计算。如果没超过 $k$，$B$ 的 $(B,j,k)$ 贡献 $\le \frac{k}{B}$。后边只需要前 $\frac{k}{B}$ 小的 $(j,k)$ 对，$O(\frac{k}{B}\log n)$ 预处理。

### [L. Largest Triangle](https://qoj.ac/contest/1738/problem/9124)

取相邻的 $a_i,a_{i+1},a_{i+2}$ 海伦公式计算。

### [N. Number of Abbreviations](https://qoj.ac/contest/1738/problem/9126)

对于 $l<r$ 要求 $s_l\neq s_r$。

### [Q. Quotient Sum](https://qoj.ac/contest/1738/problem/9129)

形如降序 a 挖去包括 $n$ 在内的一些位置最后上升的排列。设 $f_i$ 为前 $i$ 个且选了 $i$，有决策单调性。

## [The 3rd Universal Cup. Stage 5: Moscow](https://qoj.ac/contest/1741)

###  [A. Counting Permutations](https://qoj.ac/contest/1741/problem/9130)

模 $m1$ 和 $m2$ 相等的可以排列。

### [B. Bookshelf Tracking](https://qoj.ac/contest/1741/problem/9131)

在最后一次 ```R```  操作前维护属于前半边还是后半边。

### [E. Building a Fence](https://qoj.ac/contest/1741/problem/9134)

分类讨论先做哪些，剩下的部分填到哪里。所有方式取 min。

### [F. Teleports](https://qoj.ac/contest/1741/problem/9135)

设 $dp_{l,r}$ 为区间 $[l,r]$ 的答案，枚举 $k$ 翻转，每次要么拆成更小的两个区间要么从相等长度的区间转移而来。先做第一种转移，在最短路第二种转移。

### [G. Exponent Calculator](https://qoj.ac/contest/1741/problem/9136)

$e^x=\sum_{n=0}^{\infty}\frac{x^n}{n!}$。每个 $n$ 要两次，$\mid x\mid$ 增大精度下降。计算 $e^{\frac{x}{2^B}}$ 后平方 $B$ 次。取 $n=7,B=10$。

### [I. Marks Sum](https://qoj.ac/contest/1741/problem/9138)

在后 $2000$ 位一定存在前缀和 $\bmod 2000=0/1$。 可以写为 $2000x+y$，$x\le 1000$，传 $2x+y$ 即可。

### [K. Train Depot](https://qoj.ac/contest/1741/problem/9140)

区间加，求区间 max。线段树合并。注意到修改的特殊性，合并时如果存在 $tree_x=tag_x$ 就一定不优，返回 $v$，极大减小常数。否则需要递归到 $tree_u=tag_u$ 且 $tree_v=tag_v$ 再比较 $tree_u$ 和 $tree_v$，理论复杂度依然正确但是常数极大。

### [M. Uniting Amoebas](https://qoj.ac/contest/1741/problem/9142)

答案为 $\sum a_i-\max a_i$。

## [The 3rd Universal Cup. Stage 6: Osijek](https://qoj.ac/contest/1762)

### [A. Coprime Array](https://qoj.ac/contest/1762/problem/9167)

特判 $gcd(s,x)=1$。除非 $s$ 为奇 $x$ 为偶，两步可行。否则多一个 $1$。随机第一个数，失败时对于一个 $x$ 的质因数 $p$ 有 $u\bmod p=0$ 或 $(s-u)\bmod p=0$，成功率为 $\prod_{p|x}\frac{p-2}{p}$。

### [B. Square Locator](https://qoj.ac/contest/1762/problem/9168)

设 B 坐标为 $(x,y)$，绕 A $(0,\sqrt{OA})$  顺时针或逆时针旋转 $90$ 度得 D。联立解方程。

### [C. -is-this-bitset-](https://qoj.ac/contest/1762/problem/9169)

将 $dep_u\le 12$ 的 $a_u$ 设为 $2^{20-dep_u+1}$，能表示出所有 $512$ 的倍数。对于 $dep_u>12$ 的 $u$ 设 $dp_{u,i}$ 为 $1\to u$ 链上 $a_x$ 的背包模 $512$ 为 $i$ 最小和为多少。记录修改的位置减少空间。

### [D. Cycle Game](https://qoj.ac/contest/1762/problem/9170)

警示：一个 $3\times 3$ 的全黑矩形也不合法。

先最外层加一圈全为白。等价于时刻白色区域八连通且每个黑点都与一个白点八连通。线段树分治，初始一些边在一个前缀时间存在。到叶子时检查如果该点为黑与其八连通的黑点会不会无法与白点八连通。如果不删这个点，有些边重新合法。

### [H. Game Design](https://qoj.ac/contest/1762/problem/9174)

设 $dp_{i,j}$ 为前 $i$ 层且有 $j$ 条边跨过 $i$ 的方案数。枚举 $i$ 的出入边向前向后转移。

### [I. Geometry Hacking](https://qoj.ac/contest/1762/problem/9175)

在凹多边形是可能会死。构造 $(-1,-1)$，$(1,0)$，$(i+2,-i)$，$(0,1)$，面积都相等且最小。

### [J. Non-Interactive Nim](https://qoj.ac/contest/1762/problem/9176)

后手要使先手操作时存在二进制最高位的 $a_i$ 只有一个。即后手操作时存在二进制最高位的 $a_i$ 只有 $2$ 个，将其中一个变为 $0$。从高位往低位删即可。

### [K. String and Nails](https://qoj.ac/contest/1762/problem/9177)

每次删左下角即可，按 $(x,y)$ 排序。

### [L. All-You-Can-Eat](https://qoj.ac/contest/1762/problem/9178)

维护当前选的 $sum$，$[0,200)$ 的集合，$[200,400)$ 的集合，$[400,600)$ 的集合。$sum>600$ 一定合法，否则每次加入 $x$ 时贪心调整三个集合。

## [The 3rd Universal Cup. Stage 7: Warsaw](https://qoj.ac/contest/1774)

### [A. Bus Analysis](https://qoj.ac/contest/1774/problem/9220)

代价 $2\to 1,6\to 3$。dp 套 dp。内层 dp，设 $dp_{i,j}$ 为前 $i$ 个点，代价为 $j$ 最长向后多远。只有 $mn,mn+1,mn+2$ 的 dp 值有用。外层 dp 设 $f_{i,x,y,z}$ 为前 $i$ 个点，$mn,mn+1,mn+2$ 的 dp 值分别在 $x,y,z$。当 mn 增加时增加答案。除了最开始只有 $a+20\le b,b+20\le c$ 的三元组有用。

### [B. Missing Boundaries](https://qoj.ac/contest/1774/problem/9221)

有不确定的端点先当成 $[p,p]$。按左端点排序，记录最多最少能放多少 $(-1,-1)$。

### [E. Express Eviction](https://qoj.ac/contest/1774/problem/9224)

将横纵坐标都小于等于 $2$ 的障碍连边，等价于不存在左下边界到右上边界的路径。最小割。

### [G. Game of Geniuses](https://qoj.ac/contest/1774/problem/9226)

答案为最大的行的最小值。

### [K. Routing K-Codes](https://qoj.ac/contest/1774/problem/9230)

设 $f_u$ 为 $u$ 为根的和，$sum_u=\sum_{v\in subtree(u)} 2^{dep_v}$，$mxdep_u$ 为最大深度。换根 dp。

### [L. Random Numbers](https://qoj.ac/contest/1774/problem/9231)

$a_i$ 期望为 $\frac{n}{2}$。所以检查长度为 $[1,B]$ 和 $[\frac{n}{2}-B,\frac{n}{2}+B]$ 的区间。

## [The 3rd Universal Cup. Stage 8: Cangqian](https://qoj.ac/contest/1780)

## [B. Simulated Universe](https://qoj.ac/contest/1780/problem/8933)

设 $dp_{i,j,k}$ 为前 $i$ 个，$i$ 之前有 $j$ 个没匹配的祝福，向后能匹配 $k$ 个祝福是否可行。把 $k$ 压入状态，即 $dp_{i,j}$ 表示最大的 $k$ 是多少。

### [C. Challenge NPC](https://qoj.ac/contest/1780/problem/8934)

构造二分图，$1,4$ 为左，$2,3$ 为右，$1\to 2,4\to 3$。然后奇数为左向之前的右连边，偶数为右向除了 $2\times i-1$ 之前的左连边。

### [D. Puzzle: Easy as Scrabble](https://qoj.ac/contest/1780/problem/8935)

一个格子如果有两个方向的要求则为矛盾格子，最后为空。队列维护矛盾格子向后推。

### [E. Team Arrangement](https://qoj.ac/contest/1780/problem/8936)

注意到划分数不多，搜出来每组大小后贪心检查。按组的大小从小往大，在一个人的左端点处将他的右端点加入优先队列，对每个组优先取队列中最小的。

### [H. Permutation](https://qoj.ac/contest/1780/problem/8939)

二分，时刻维护当前区间次大值位置。如果次大值和最大值在同一边则用一次，否则两次。每次将 $len$ 变为 $d\times len$ 用 $1$ 次，$(1-d)\times len$ 用 $2$ 次，取 $d=0.6$。

### [I. Piggy Sort](https://qoj.ac/contest/1780/problem/8940)

按位置之和排序，可以知道每张照片的先后顺序。$m>n$ 所以必然有一只猪出现在相邻照片的同一位置。枚举这个位置，检查是否存在这样一条直线经过 $m$ 个点。每只猪只可能出现在一条直线上。

### [J. Even or Odd Spanning Tree](https://qoj.ac/contest/1780/problem/8941)

找到最小生成树，只替换一条边，维护奇偶边权的路径最大值。

### [L. Challenge Matrix Multiplication](https://qoj.ac/contest/1780/problem/8943)

每次找一条从 $d_u>0$ 到 $d_v<0$ 的路径，$\sum |in_u-out_u|$ 减少 $2$。对于一条路径，$a_i$ 的答案包含 $a_{i+1}$ 的答案。从 $v$ 到 $u$ 依次 bfs 计算答案增量，每个点只经过一次。

## [The 3rd Universal Cup. Stage 9: Xi'an](https://qoj.ac/contest/1784)

### [A. An Easy Geometry Problem](https://qoj.ac/contest/1784/problem/9242)

差分，哈希 $a_i$ 和反过来的 $k-a_i$。线段树维护哈希值。二分答案。

### [E. Dominating Point](https://qoj.ac/contest/1784/problem/9246)

出度最大的点 $u$ 为支配点。设 $u$ 连向 $S$，$T$ 连向 $u$。如果存在 $x$ 使得 $dis(u,x)>2$，那么 $x$ 连向所有 $S$ 和 $u$，$d_x>d_u$，矛盾。如果 $T$ 为空，无解。否则 $T$ 组成的子图的支配点 $uu$ 也符合条件。如果 $uu$ 不是指向 $T$ 所有点，递归下去得到 $uuu$。否则指向 $uu$ 且属于 $S$ 的部分的支配点符合条件。

### [F. An Easy Counting Problem](https://qoj.ac/contest/1784/problem/9247)

lucas 定理，等价于拆成 $p$ 进制数下每一位的组合数之积。设 $dp_{i,j}$ 为填到前 $i$ 位，组合数之积为 $j$，$cnt_k$ 为一位时的答案。$dp_{i,j}=\sum_{kl\mod p=j} dp_{i,k}\times cnt_l$。满足结合律，快速幂优化。$p$ 为质数有原根，下标 $i$ 改为 $g^x\bmod p=i$ 的 $x$，加法卷积。

### [H. Elimination Series Once More](https://qoj.ac/contest/1784/problem/9249)

从小到大加入，每次更新 $n$ 个点。

### [I. Max GCD](https://qoj.ac/contest/1784/problem/9250)

质因数分解，枚举答案。可能贡献的 $(i,j,k)$ 满足 $i,j$ 是相邻的 $v$ 的倍数，双指针最近的 $k$。共 $O(n\sqrt n)$ 组。把 $(k,v)$ 挂在 $i$ 上，二位数点，做 $O(1)$ 插入 $O(\sqrt n)$ 查询的分块。

### [J. Graph Changing](https://qoj.ac/contest/1784/problem/9251)

$>3$ 一次后无解，分讨 $n$ 和 $t$。