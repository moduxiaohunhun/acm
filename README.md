# acm
Problem E : Il Gioco dell'X
WA
#include <iostream>

using namespace std;
char area[200][200];
char ch='\0';
int n;
void dfs(int a,int b)
{
    ch=area[a][b];
    area[a][b]='.';
    if(a<n-1&&area[a+1][b]==ch)
    {
        dfs(a+1,b);
    }
    else if(b<n-1&&area[a][b+1]==ch)
    {
        dfs(a,b+1);
    }
    else if(b>0&&area[a][b-1]==ch)
    {
        dfs(a,b-1);
    }
    else if(a<n-1&&b<n-1&&area[a+1][b+1]==ch)
    {
        dfs(a+1,b+1);
    }
}
int main()
{
   int sum=1;
   int flag;
   while(cin>>n&&n!=0)
   {
       flag=0;
       for(int i=0;i<n;i++)
       {
           for(int j=0;j<n;j++)
           {
               cin>>area[i][j];
           }
       }
       for(int j=0;j<n;j++)
       {
               ch=area[0][j];
               if(ch=='b')
               {
                   dfs(0,j);
               }
       }
       for(int k=0;k<n;k++)
       {
           if(area[n-1][k]=='.')
           {
               cout<<sum<<" B"<<endl;
               flag=1;
               break;
           }
       }
       if(flag==0)
       {
           cout<<sum<<" W"<<endl;
       }
       sum++;
   }
    return 0;
}
