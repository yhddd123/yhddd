## The 3rd Universal Cup. Stage 10: West Lake 题解

[https://www.cnblogs.com/yhddd/p/18438358](https://www.cnblogs.com/yhddd/p/18438358)

第一场 ucup，被创飞了。

![image](https://img2024.cnblogs.com/blog/3442478/202409/3442478-20240928203249709-698107884.png)

WRuperD 正开，我，dieselhuang 倒开。

20 min 有人过 A 了，计算几何，WRuperD 让我去看。一看就“会了“，51 min 交了，挂了，于是连吃了 $6$ 发罚时。1.5h 发现想少了一种情况，2h 过了。一题队垫底。

跟 WRuperD 胡了一下 C 交互，感觉很对，就让他去写了。dieselhuang 询问 M 的 ```map<int,vector<int>> a[maxn]``` 会不会爆，感觉很抽象。跟榜 D，一看就“会了“，但是是 $10^6$ 的双 $\log$。2h20min 时 C 交了，次数爆了 $500$。要自信，3h 交 D T 了。一下感觉自己小丑了，随便优化掉一个 $\log$，3h12min 过了。两题队倒数第二。

再交流了一下 C，在 WRuperD 的基础上我觉得可以接着优化，于是 WRuperD 去看 dieselhuang 的 M。于是接手 C 的代码，感觉码风兼容性极低，删掉了 4k 代码自己又写了 4k，4h18min 交了过了。三题队垫底。

然后去看 dieselhuang 的 M，看不懂，但感觉很对啊，然后时间就没了。

赛后看 K ，计算几何，一看就会了，挂了 5 发，30min 就过了。

我觉得队名应该改为 **ucup 罚时大王**。

### [A. Italian Cuisine](https://contest.ucup.ac/contest/1803/problem/9434)

复制一遍，枚举 $i$ 维护右端点 $j$。要求 $(x,y)$ 到过 $(a_i,b_i),(a_j,b_j)$ 的直线距离大于 $r$ 或 等于 $r$ 且交点不在线段上，即 $\angle OIJ$ 和 $\angle OJI$ 至少一个为钝角，即两个向量的数量积小于零。要求 $(a_i,b_i),(x,y),(a_j,b_j)$ 的夹角和 $(a_i,b_i),(x,y),(a_{j-1},b_{j-1})$ 的夹角同正负，即两个向量的叉积同正负。三点坐标求面积 $S=\frac{\lvert x1y2+x2y3+x3y1-x1y3-x2y1-x3y2\rvert}{2}$。

### [C. Permutation](https://contest.ucup.ac/contest/1803/problem/9432)

大概在 $\frac{2}{3}n\log n$ 级别。线段树维护区间 $[l,r]$ 有什么数，每次随机取出两个数，将左半边设为 $u$，右半边设为 $v$ 询问。如果 $ans=0/2$ 可以将 $u,v$ 放入左右儿子，否则如果这是第一次，就把 $u,v$ 放回去重来，否则一定找得到一个数 $x$，将某半边设为 $x$ 再问一遍。理论上是 $\frac{3}{4}n\log n$，加上剪枝次数就差不多刚好了，偶尔会超。

![image](https://img2024.cnblogs.com/blog/3442478/202409/3442478-20240928213403784-1295343403.png)

### [D. Collect the Coins](https://contest.ucup.ac/contest/1803/problem/9427)

按 $t_i$ 排序，二分答案 $x$。设 $dp_{i,j}$ 为前 $i$ 个询问，另一个人在询问 $j$。如果 $\lvert p_i-p_{i-1}\rvert\le x\times (t_i-t_{i-1})$，$dp_{i,j}$ 继承 $dp_{i-1,j}$。然后再考虑 $j$ 更新 $dp_{i,i-1}$。拆绝对值有 $p_i+xt_i\ge p_j+xt_j$ 且 $p_i-ct_i\le p_j-xt_j$。维护对应的 $mn$ 和 $mx$ 即可。

### [K. Palindromic Polygon](https://contest.ucup.ac/contest/1803/problem/9417)

复制一遍，设 $dp_{i,j,0/1/2}$ 为区间 $[i,j]$ 中选了 $i,j$ 且是回文串、除了 $i$ 是回文串，除了 $j$ 是回文串的最大面积。
