# 并查集Union-Find

> F：找根
>
> U：合并

## 模板

```c++
class UF
{
public:
    int *root;
    int count;

    UF(int count)
    {
        this->count=count;
        root=new int[count];
        for(int i=0;i<=count-1;i++)
            root[i]=i;                  //初始化，独立成集合
    }
    
    int findRoot(int index)
    {
        if(root[index]==index)
            return index;

        int _root=findRoot(root[index]);
        root[index]=_root;	//路径简化
        return _root;
    }

    void Union(int a,int b)		//合并
    {
        int rootA=findRoot(a);
        int rootB=findRoot(b);
        if(rootA==rootB)
            return;
        else
            root[rootA]=rootB;
    }
    
    int countSet()
    {
        int ans=0;
        for(int i=0;i<=count-1;i++)
        {
            if(root[i]==i)	//找根节点
                ans++;
        }
        return ans;
    }

};
```

```java
class UF
{
    int n;
    int[] parent;
    int[] size;
    int setCount;

    public UF(int n)
    {
        this.n=n;
        this.setCount=n;
        this.parent=new int[n];
        this.size=new int[n];

        for(int i=0;i<=n-1;i++)
        {
            parent[i]=i;
            size[i]=1;
        }
    }
    public int find(int a)
    {
        return a==parent[a]? a:(parent[a]=find(parent[a]));
    }
    public boolean isConnceted(int a,int b)
    {
        return find(a)==find(b);
    }
    public boolean unite(int a,int b)
    {
        a=find(a);b=find(b);
        if(a==b)  return false;

        if(size[a]<size[b])
        {
            a=a+b;b=a-b;a=a-b;  //优雅地交换两个数
        }
        size[a]+=size[b];
        parent[b]=a;
        setCount--;
    }

}
```



## 例题

### LeetCode 947  拿棋子

```C++
class Point
{
public:
    int x,y;
    
    bool isConnected(Point &p)		//判断是否要union
    {
        return (this->x==p.x|| this->y==p.y);
    }
};
```

```C++
class Solution {
public:
    vector<Point>points;
    int removeStones(vector<vector<int>>& stones)
    {
        UF uf(stones.size());
        for(auto stone:stones)
        {
            Point tem={stone[0],stone[1]};
            points.push_back(tem);
            for(int i=0;i<=points.size()-1;i++)
                if(tem.isConnected(points[i]))
                    uf.Union(points.size()-1,i);
        }
        return stones.size()-uf.countSet();
    }
};
```



### LeetCode 803  打砖块

### [LeetCode 959 斜杠划分](https://leetcode-cn.com/problems/regions-cut-by-slashes/solution/you-xie-gang-hua-fen-qu-yu-by-leetcode-67xb/)