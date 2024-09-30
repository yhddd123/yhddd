[AT_dp_j](https://www.luogu.com.cn/problem/AT_dp_j)

### 思路

期望 dp。

设 $dp_{i,j,k,l}$ 表示当前有 $0,1,2,3$ 个寿司的盘子数有 $i,j,k,l$ 个时的期望次数。

显然 MLE。但可以发现 $i+j+k+l=n$，所以可以去掉一维。

设 $dp_{i,j,k}$ 表示当前有 $1,2,3$ 个寿司的盘子数有 $i,j,k$ 个时的期望次数。

首先有 $dp_{0,0,0}=0$。

对于一个状态 $dp_{i,j,k}$ 可以有四个状态得到。可以选装了 $1,2,3$ 个寿司的盘子，或者选空盘子，即浪费一步。

所以有：

$dp_{i,j,k}=\frac {i}{n}\times dp_{i-1,j,k}+\frac {j}{n}\times dp_{i+1,j-1,k}+\frac {k}{n}\times dp_{i,j+1,k-1}+\frac {n-i-j-k}{n}\times (dp_{i,j,k}+1)$

左右两边都有 $dp_{i,j,k}$，进行移项。得到：

$\frac {i+j+k}{n}\times dp_{i,j,k}=\frac {i}{n}\times dp_{i-1,j,k}+\frac {j}{n}\times dp_{i+1,j-1,k}+\frac {k}{n}\times dp_{i,j+1,k-1}+\frac {n-i-j-k}{n}$

$dp_{i,j,k}=(\frac {i}{n}\times dp_{i-1,j,k}+\frac {j}{n}\times dp_{i+1,j-1,k}+\frac {k}{n}\times dp_{i,j+1,k-1}+\frac {n-i-j-k}{n}) \times \frac {n}{i+j+k}$

$dp_{i,j,k}=\frac {i}{i+j+k}\times dp_{i-1,j,k}+\frac {j}{i+j+k}\times dp_{i+1,j-1,k}+\frac {k}{i+j+k}\times dp_{i,j+1,k-1}+\frac {n-i-j-k}{i+j+k}$

但是 $dp_{i,j,k}$ 需要由 $dp_{i-1,j,k},dp_{i+1,j-1,k},dp_{i,j+1,k-1}$ 计算，不符合正常理解里的 dp。所以设 $dp_{k,j,i}$ 表示当前有 $3,2,1$ 个寿司的盘子数有 $k,j,i$ 个时的期望次数。改变枚举次序，先枚举 $k$，再枚举 $j$，最后再枚举 $i$。

代码不长。

### code

```cpp
signed main(){
	n=read();
	for(int i=1;i<=n;i++)a[i]=read(),cnt[a[i]]++;
	dp[0][0][0]=0;
//	cout<<cnt[1]<<" "<<cnt[2]<<" "<<cnt[3]<<"\n";
	for(int k=0;k<=n;k++){
		for(int j=0;j<=n;j++){
			for(int i=0;i<=n;i++){
				if(i||j||k){
					dp[k][j][i]=1.0*(n-i-j-k)/(i+j+k);
					if(i)dp[k][j][i]+=1.0*i/(i+j+k)*(dp[k][j][i-1]+1);
					if(j)dp[k][j][i]+=1.0*j/(i+j+k)*(dp[k][j-1][i+1]+1);
					if(k)dp[k][j][i]+=1.0*k/(i+j+k)*(dp[k-1][j+1][i]+1);
//					cout<<i<<" "<<j<<" "<<k<<" ";
//					printf("%10lf\n",dp[k][j][i]);
				}
			}
		}
	}
	printf("%.10lf",dp[cnt[3]][cnt[2]][cnt[1]]);
}
```