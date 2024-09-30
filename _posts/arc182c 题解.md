[arc182c](https://www.luogu.com.cn/problem/AT_arc182_c)

### 思路
有 $6$ 个小于 $14$ 的质数，设这 $6$ 个质数的指数分别为 $x_1,\dotsb,x_6$。$ans=\sum (\prod_{i=1}^d (x_i+1))$。状压这 $6$ 个数，维护 $val_s=\prod_{i=1}^6 (x_i\times [s二进制第 i位为1]+[s二进制第 i位为0])$。当加入一个数时，某些 $x_i$ 会加 $d$，$s$ 二进制第 $i$ 位为 $1$ 的 $val_s$ 会从 $s$ 的子集且一些二进制第 $i$ 位为 $0$ 的 $t$ 的 $val_t$ 转移来。

矩阵快速幂维护转移。额外维护一个位置 $p$ 表示答案之和，所有的 $e[s][p]=1$。 

### code
```cpp
int n,m,l=64;
struct mat{
	int e[66][66];
	mat(){
		for(int i=0;i<=l;i++){
			for(int j=0;j<=l;j++)e[i][j]=0;
		}
	}
	mat operator*(const mat&tmp)const{
		mat res;
		for(int i=0;i<=l;i++){
			for(int j=0;j<=l;j++){
				for(int k=0;k<=l;k++)(res.e[i][j]+=e[i][k]*tmp.e[k][j])%=mod;
			}
		}
		return res;
	}
}bas,mul;
mat one(){
	mat res;
	for(int i=0;i<=l;i++)res.e[i][i]=1;
	return res;
}
mat ksm(mat a,int b){
	mat ans=one();
	while(b){
		if(b&1)ans=ans*a;
		a=a*a;
		b>>=1;
	}
	return ans;
}
int pre[6]={2,3,5,7,11,13};
void work(){
	n=read();m=read();
	mul.e[0][0]=1;
	for(int s=0;s<l;s++)bas.e[s][l]=1,bas.e[s][s]=m;
	bas.e[l][l]=1;
	for(int i=1;i<=m;i++){
		for(int s=0;s<l;s++){
			for(int t=1;t<=s;t++)if((s&t)==t){
				bool fl=1;
				for(int j=0;j<6;j++)if(i%pre[j]!=0&&(t&(1<<j)))fl=0;
				if(!fl)continue;
				int val=1,x=i;
				for(int j=0;j<6;j++)if(t&(1<<j)){
					int cnt=0;
					while(x%pre[j]==0)x/=pre[j],++cnt;
					val=val*cnt;
				}
				bas.e[s^t][s]+=val;
			}
		}
	}
	mul=mul*ksm(bas,n+1);
	printf("%lld\n",mul.e[0][l]-1);
}
```