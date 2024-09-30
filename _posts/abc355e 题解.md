[abc355e](https://www.luogu.com.cn/problem/AT_abc355_e)

### 思路

[WC2024T3](https://www.luogu.com.cn/problem/P10145) 中知道一个技巧：如果知道区间 $[l,r]$ 的和就连边 $l\to r+1$，那么想推出 $[L,R]$ 的区间和就要求 $L$ 和 $R+1$ 联通。

按题意把符合要求的边连上，设边权为 $1$ 跑 bfs，求出 $L$ 到 $R+1$ 的最短路并记录路径上的点，就可以得到要询问的区间。

因为是从小往大推，对于最短路上的边 $u\to v$，如果 $u<v$ 就把区间和加上，否则减去。

### code

```cpp
int n,a,b;
int dis[maxn],pre[maxn];
vector<pii> ans;int res;
queue<int> q;
signed main(){
	n=read();a=read();b=read();
	mems(dis,0x3f);dis[a]=0;q.push(a);
	while(!q.empty()){
		int u=q.front();q.pop();
		for(int i=1;i<=(1<<n);i<<=1){
			int v=u+i;
			if(u%i==0&&v<=(1<<n)){
				if(dis[v]>dis[u]+1)dis[v]=dis[u]+1,pre[v]=u,q.push(v);
			}
			v=u-i;
			if(v%i==0&&v>=0){
				if(dis[v]>dis[u]+1)dis[v]=dis[u]+1,pre[v]=u,q.push(v);
			}
		}
	}
	// cout<<dis[0]<<" "<<dis[8]<<"\n";
	int u=b+1;
	while(u!=a){
		ans.push_back({pre[u],u});
		u=pre[u];
	}
	for(auto [l,r]:ans){
		int i=log2(abs(l-r)),j=min(l,r)/abs(l-r);
		if(l<r){
			printf("? %lld %lld\n",i,j);fflush(stdout);
			res+=read();
		}
		else{
			printf("? %lld %lld\n",i,j);fflush(stdout);
			res-=read();
		}
	}
	res%=100,res+=100,res%=100;
	printf("! %lld\n",res);fflush(stdout);	
}
```