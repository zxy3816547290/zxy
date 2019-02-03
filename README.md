#include<stdio.h>
#include<algorithm>
using namespace std;
bool cmp(int a,int b)
{
	return a<b;
}
void main()
{
	int a[4][4];
	int b[16];
	int m,n,i=0;
	for(m=0;m<4;m++)
	{
		for(n=0;n<4;n++)
		{
			scanf("%d",&a[m][n]);
		}
	}
	for(m=0;m<4;m++)
	{
		for(n=0;n<4;n++)
		{
			b[i++]=a[m][n];
		}
	}
	sort(b,b+16,cmp);
	printf("%d %d",b[1],b[14]);
}

