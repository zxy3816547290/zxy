#include<stdio.h>
#include<math.h>
int prime[1000];
int yinshu1[1000];
int yinshu2[1000];
bool unprime=false;
int c=0;
int power(int a,int k)
{
	if(k==0) return 1;
	else return a*power(a,k-1);
}
void init()
{
	int i,k=0,j;
	for(i=2;i<=1000;i++)
	{
		k=int(sqrt(i))+1;
		for(j=2;j<=k;j++)
		{
			if(i%j==0)
			{
				unprime=true;
				break;
			}
		}
		if(unprime==false)
		{
			prime[c++]=i;
		}
		unprime=false;
	}
}
void main()
{
	init();
	int n,a,i=0,t=0,j=0,k=1;
	while(scanf("%d%d",&n,&a)!=EOF)
	{
		int ans=10000;
		t=n;
		for(i=0;i<c;i++)
		{
			while(t>0)
			{
		    	j=t/power(prime[i],k);
		    	yinshu1[i]+=j;
		    	k++;
		    	t=n;
		    	if(j==0) break;
			}
			t=n;
			k=1;
		}		
		t=a;
		i=0;
		for(i=0;i<c;i++)
		{
			while(t%prime[i]==0)
			{
				t/=prime[i];
	     		yinshu2[i]++;
			}
		}	
		for(i=0;i<c;i++)
		{
			if(yinshu2[i]==0) continue;
			if(ans>yinshu1[i]/yinshu2[i])
			{
				ans=yinshu1[i]/yinshu2[i];
			}
		}
		printf("%d",ans);
	}
}
