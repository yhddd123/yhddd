[abc146e](https://www.luogu.com.cn/problem/AT_abc146_e)

### 思路

由题，$k\mid (a_l+a_{l+1}+...+a_{r-1}+a_r)-(r-l+1)$，可以转换为平均每个数在模 $k$ 下都贡献了 $1$。所以对区间每个数都减 $1$，则长度为 $len$ 的区间和减了 $len$，此时如果区间和为 $k$ 的倍数则符合条件。

预处理对 $k$ 取模的前缀和 $sum_i$，如果 $sum_{l-1}=sum_r$，则区间 $[l,r]$ 符合条件。又因为 $r-l+1<k$，所以 $r-(l-1)+1\leq k$。

所以 $i$ 的 $sum_i$ 对答案的贡献为 $i-k+1\leq j\leq i-1$ 中与 $sum_i$ 相等的 $sum_j$ 的个数。

$sum_i$ 值域大，不能用桶处理。用 map 处理，删除 $sum_{i-k}$ 过期的，统计答案，加入 $sum_i$。

注意最开始的 $sum_0=0$ 也要算。

### code

```cpp
int n,k,a[maxn];
map<int,int> mp;
int ans;

int T;
signed main(){
//	freopen(".in","r",stdin);
//	freopen(".out","w",stdout);

	n=read();k=read();
	mp[0]++;
	for(int i=1;i<=n;i++){
		a[i]=read();
		a[i]+=k-1;a[i]%=k;//a[i]+k-1=a[i]-1，在模 k 时。
		a[i]+=a[i-1];a[i]%=k;
		if(i>=k)mp[a[i-k]]--;
		ans+=mp[a[i]];
		mp[a[i]]++;
	}
	printf("%lld\n",ans);
}
```