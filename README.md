# Cow Sheep problem in C
Finding number of cows and sheeps in a 2D area.



#include<stdio.h>
#include<string.h>
#include<math.h>
#include<stdlib.h>

int r,c,res,count=0,res=0;

int func(char str[][100],int row,int col);

int main()
{
	char str[100][100];

	int i,j,a[10];

	float val;
	printf("Enter r and c\n");
	scanf("%d%d",&r,&c);

	for(i=0;i<r;i++)
		scanf("%s",str[i]);

	
	for(i=0;i<r;i++)
	{
		for(j=0;j<c;j++)
		{
			if(func(str,i,j)>0)
				count++;
		}
	}
	//binary(a,count-1);
	res=pow(2,count-1);
	printf("%d\n",res);	
	return 0;	
}

int func(char str[][100],int row,int col)
{
	if(row>r-1||col>c-1)
		return 0;
	
	if(str[row][col]=='N')
		return 0;
	
	else if(str[row][col]=='Y')
	{
		str[row][col]='N';
		return 1+func(str,row+1,col)+func(str,row,col+1)+func(str,row-1,col)+func(str,row,col-1);
	}
}

int binary(int a[],int n)
{
        int x=0,i;
        if(n<0)
        {
                for(i=0;i<count;i++)
                {
                        if(a[i]==0)
                                x++;
                }
                if(x%2==0)
                {
                        res++;
                }
        }
        else
        {
                a[n]=0;
                binary(a,n-1);
                a[n]=1;
                binary(a,n-1);
        }

}

