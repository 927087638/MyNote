# DP

> 类似于递推函数，不一定是一维的~

## 回文串

### 记录回文区间

```java
        dp = new boolean [n][n];

        for(int i=0;i<n;i++)
            Arrays.fill(dp[i],true);   //提前全置为true,考虑到 l>r 的情况(不是下表相等能解决的问题

        for(int i=n-1;i>=0;i--)
        {
            for(int j=i+1;j<n;j++)
                dp[i][j] = (s.charAt(i)==s.charAt(j))&&(dp[i+1][j-1]); 
            	//i+1这个地方决定了，i要倒序遍历(--),因为要准备好较大值
        }
```

#### [分割回文串](https://leetcode-cn.com/problems/palindrome-partitioning/)

dp + traceback

```java
class Solution {
    boolean [][]dp;
    List<List<String>> ans_s;
    List<String> ans;
    int n;

    public List<List<String>> partition(String s) {
        n=s.length();
        dp = new boolean [n][n];
        ans_s=new ArrayList<List<String>>();
        ans = new ArrayList<String>();

		........

        traceback(s,0);

        return ans_s;
    }

    void traceback(String s,int start)
    {
        if(start == n)
        {
            ans_s.add(new ArrayList<String>(ans));
            return;
        }

        for(int i=start;i<n;i++)
            if(dp[start][i])
            {
                ans.add(s.substring(start,i+1));
                traceback(s,i+1);
                ans.remove(ans.size()-1);
            }
    }

}
```

#### [分割回文串 II](https://leetcode-cn.com/problems/palindrome-partitioning-ii/)

dp + 贪心

```java
class Solution {
    public int minCut(String s) {
        int  n=s.length();
        
        ........
            
        int[] before = new int[n];
        for(int i=0;i<n;i++)
        {
            if(dp[0][i])
                before[i] = 0;
            else
                for(int j=0;j<i;j++)
                {
                    if(dp[j+1][i])
                        before[i] = Math.min(before[j]+1,before[i]);
                }
        }

        return before[n-1];
    }
}
```

