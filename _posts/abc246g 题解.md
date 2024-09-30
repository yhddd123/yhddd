[abc246g](https://www.luogu.com.cn/problem/AT_abc246_g)

### 思路

最少拿分，考虑二分答案。

B 最少拿 $mid$ 分，则 A 需要在 B 之前改变所有 $a_u\geq mid$ 的点。

显然 B 不会走回头路。

设 $f_u$ 表示：B 在 $u$ 点并向其儿子之一 $v$ 移动前，A 需要对 $u$ 的子树操作几次使 B 无法成功。如果 $f_u\geq 1$，就意味着当 A 在到达 $u$ 之前就要提前在 $u$ 的子树内做准备。如果 $f_u\leq 0$，说明 $u$ 的子树内 A 必胜，但 $f_u$ 不能向上转移负数，所以 $f_u=\max(f_u,0)$。否则 B 必胜。

B 可以去任意的 $v$ 且无法预测，所以 $f_u=\sum f_v$ 。又因为 A 先手，A 在 B 移动前可以操作一次,$f_u$ 加 $1$，但如果 $a_u\geq mid$，$f_u$ 减 $1$。

$$f_u=\max(\sum f_v-1,0)+(a_u\geq mid))$$

从 $1$ 开始 dfs 搜索。如果 $f_1\geq 1$，说明此时 B 必胜。

### code

```cpp
int n,a[maxn],f[maxn];
int head[maxn],tot;
struct nd{
	int nxt,to;
}e[maxn<<1];
void add(int u,int v){
	e[++tot].nxt=head[u];
	e[tot].to=v;
	head[u]=tot;
}
int l,r,mid,ans,mx;

void dfs(int u,int fa,int x){
	int sum=0;
	for(int i=head[u];i;i=e[i].nxt){
		int v=e[i].to;
		if(v!=fa){
			dfs(v,u,x);
			sum+=f[v];
		}
	}
	if(sum)--sum;
	f[u]=sum+(a[u]>=x);
}
bool check(int x){
	dfs(1,0,x);
	return f[1]!=0; 
}

int T;
signed main(){
//	freopen(".in","r",stdin);
//	freopen(".out","w",stdout);

	n=read();
	for(int i=2;i<=n;i++){
		a[i]=read();
		if(mx<a[i])mx=a[i];
	}
	for(int i=1;i<n;i++){
		int u,v;u=read();v=read();
		add(u,v);add(v,u);
	}
	int l=1,r=mx;
	while(l<=r){
		mid=l+r>>1;
		if(check(mid)){
			l=mid+1;
			ans=mid;
		}
		else r=mid-1;
	}
	printf("%lld\n",ans);
}
```