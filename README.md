# SUMMINGPIECES
# QUESTION

    https://www.hackerrank.com/contests/world-codesprint-7/challenges/summing-pieces
    
*********************************************************************************************************************************
# SOLUTION

    #include <iostream>

    using namespace std;

    int main()
    {
        long long int n,fact[1000001],a[1000001],MOD=1000000007,i,c,count=0,z,k,p;
        cin>>n;
        fact[0]=1;
        fact[1]=1;
        for(i=2;i<=n;i++)
            fact[i]=(2*fact[i-1])%MOD;
        c=0;
        for(i=1;i<=n;i++)
            c=(c+(i*fact[n-i]))%MOD;
        for(i=0;i<n;i++)
            cin>>a[i];
        k=1;
        p=c;
        if(n==1)
            cout<<a[0];
        else if((n%2)==0)
        {
            for(i=0;i<(n/2);i++)
            {
                z=(a[i]+a[n-i-1])%MOD;
            
                count=(count+(z*p))%MOD;
                p=(p+fact[n-i-1]-k);
                if(p<0)
                {while(p<0)
                    {
                    p+=MOD;
                }
                }
                else
                    p%=MOD;
                k=(k*2)%MOD;
        
            }
            cout<<count;
        }
        else
        {
            for(i=0;i<=(n/2);i++)
            {
                if((i==(n/2))&&((2*i)!=(n/2)))
                    z=a[i];
                else
                    z=(a[i]+a[n-i-1])%MOD;
          
                count=(count+(z*p))%MOD;
                p=(p+fact[n-i-1]-k);
                if(p<0)
                {while(p<0)
                    {
                    p+=MOD;
                }
                }
                else
                    p%=MOD;
                k=(k*2)%MOD;
        
            }
            cout<<count;
        }
        return 0;
    }
