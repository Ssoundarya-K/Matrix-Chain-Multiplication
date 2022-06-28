# Matrix-Chain-Multiplication
Given a sequence of matrices. There are many different possibilities to perform their multiplication. Find the most efficient order to multiply these matrices together. Also give the least number of multiplications required.
code:
#include<iostream>
using namespace std;

void matrix_mul(int p[],int n)
{
    int a[n][n]={0};
    for(int d=1;d<n-1;d++)
    {
        for(int i=1;i<n-d;i++)
        {
            int j=i+d;
            int min=32767;
            for(int k=i;k<=j-1;k++)
            {
                int cost=a[i][k]+a[k+1][j]+p[i-1]*p[k]*p[j];
                if(cost<min)
                {
                    min=cost;
                }
            }
            a[i][j]=min;
        }
    }
    cout<<"The minimum number of multiplications is: ";
    cout<<a[1][n-1]<<endl;
}
int main()
{
    int n;
    cout<<"Enter the number of matrices\n";
    cin>>n;
    int p[n];
    cout<<"Enter the order of matrices\n";
    for(int i=0;i<n;i++)
    {
        cin>>p[i];
    }
    matrix_mul(p,n);
    return 0;
}
