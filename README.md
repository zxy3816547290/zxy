#include<stdio.h>
#include<string.h>
struct biginteger{
	int digit[1000];
	int size;
	void init()
	{
		int i;
		for(i=0;i<1000;i++)
		{
			digit[i]=0;
		}
		size=0;
	}
	void set(int x)
	{
		init();
		while(x>0)
		{
			digit[size++]=x%10000;
			x/=10000;
		}
	}
	biginteger operator *(int a) const
	{
		biginteger r;
		r.init();
		int i,carry=0,tmp;
		for(i=0;i<size;i++)
		{
			tmp=digit[i]*a+carry;
			carry=tmp/10000;
			tmp%=10000;
			r.digit[r.size++]=tmp;
		}
		if(carry!=0)
		{
			r.digit[r.size++]=carry;
		}
		return r;
	}
	void output()
	{
		int i;
		for(i=size-1;i>=0;i--)
		{
			if(i!=size-1) printf("%4d",digit[i]);
			else printf("%d",digit[i]);
		}
		printf("\n");
	}
}a;
void main()
{
	int i,n;
	while(scanf("%d",&n)!=EOF)
	{
		a.init();
		a.set(1);
		for(i=1;i<=n;i++)
		{
			a=a*i;
		}
		a.output();
	}
}
