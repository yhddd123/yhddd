[AT_joi2020ho_b](https://www.luogu.com.cn/problem/AT_joi2020ho_b)

另，这道题也是 [P6878](https://www.luogu.com.cn/problem/P6878)，数据应该是强一些。

### 思路

枚举起始的位置 $i$，显然 $c[i]=J$，即枚举 $J$ 的位置。为了使操作三删除中间的字符更少，问题转换对于为从 $i$ 起的最短的包含一个 $k$ 阶字符串的字符串的长度。有点绕。

那么从 $i$ 位置起，向后找 $k-1$ 个 $J$，记录位置 $res$。再找 $res$ 之后第一个 $O$，同理再找 $I$，记录$k$ 个 $I$ 之后的位置 $res$，计算答案：

$ans=\min(ans,res-i+1-3\times k)$

---

到具体实现，分别记录 $J$,$O,$I$ 的编号，记录每个 $J$,$O$ 后最近的 $O$,$I$，用 $O(1)$ 得出每个答案并取最小值。$pos[i]$ 记录第 $i$ 个（编号）同种字符的位置，$nxt[i]$ 表示位置 $i$ 处的字符下一种字符的编号。

### code

```cpp
int n,k;
char c[maxn];
int pos[maxn][5],nxt[maxn][3];
int cnt1,cnt2,cnt3,cnt;
int res,mx,ans=1000000;
signed main(){
	scanf("%d%d%s",&n,&k,c+1);
	for(int i=1;i<=n;i++){
		if(c[i]=='J'){
			pos[++cnt1][1]=i;
		}
		if(c[i]=='O'){
			pos[++cnt2][2]=i;
			cnt=cnt1;
			while(!nxt[pos[cnt][1]][2] && cnt)nxt[pos[cnt][1]][2]=cnt2,cnt--;
		}
		if(c[i]=='I'){
			pos[++cnt3][3]=i;
			cnt=cnt2;
			while(!nxt[pos[cnt][2]][3] && cnt)nxt[pos[cnt][2]][3]=cnt3,cnt--;
		}
	}
	for(int i=1;i+k-1<=cnt1;i++){
//		cout<<pos[i][1]<<" ";
		//pos[i][1] 第一个J的位置 
		res=pos[i+k-1][1];//最后一个J的位置 
//		cout<<res<<" ";
		res=nxt[res][2];//第一个O的编号 
//		cout<<res<<" ";
		if(res+k-1>cnt2 || !res){
//			cout<<"\n";
			continue;
		}
		res=pos[res+k-1][2];//最后一个O的位置
//		cout<<res<<" ";
		if(!res){
//			cout<<"\n";
			continue;
		}
		res=nxt[res][3];//第一个I的编号 
//		cout<<res<<" ";
		if(res+k-1>cnt3 || !res){
//			cout<<"\n";
			continue;
		}
		res=pos[res+k-1][3];//最后一个I的位置
//		cout<<res<<endl;
		if(!res){
			continue;
		}
		ans=min(res-pos[i][1]+1-3*k,ans);
	}
	if(ans==1000000)printf("-1\n");
	else printf("%d\n",ans);
}
```

-  while 均摊应该是 $O(1)$。
