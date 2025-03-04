# march4_2025
The problem that i solved today in leetcode

1.Given an integer n, return true if it is possible to represent n as the sum of distinct powers of three. Otherwise, return false.

An integer y is a power of three if there exists an integer x such that y == 3x.

Code:
class Solution {
    public boolean f(int ind,List<Integer> l,int target)
    {
        if(ind==l.size())
        {
            if(target==0)
                return true;
            return false;
        }
        boolean nt=f(ind+1,l,target);
        boolean t=false;
        if(target>=l.get(ind))
            t=f(ind+1,l,target-l.get(ind));
        return nt||t;
    }
    public boolean checkPowersOfThree(int n) {
        int x=1;
        int z=0;
        List<Integer> l=new ArrayList<>();
        while(x<=n)
        {
            l.add(x);
            x*=3;
            z++;
        }
        return f(0,l,n);
    }
}
