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
    int setNumber;  //集合个数

    UF(int count)
    {
        this->count=count;
        this->setNumber=count;
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

    bool Union(int a,int b)		//合并
    {
        int rootA=findRoot(a);
        int rootB=findRoot(b);
        if(rootA==rootB)
            return false;
        else
            root[rootA]=rootB;
            setNumber--;
            return true;
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

### [LeetCode 765 情侣牵手](https://leetcode-cn.com/problems/couples-holding-hands/)

**「至少交换的次数 = 所有情侣的对数 - 并查集里连通分量的个数」**

```c++
class Solution {
public:
    int minSwapsCouples(vector<int>& row) 
    {
        int N=row.size()/2;
        UF uf(N);
        for(int i=0;i<N;i++)
        {
            uf.Union(row[2*i]/2,row[2*i+1]/2);
        }
        return N-uf.setNumber;
    }
};
```



### LeetCode 803  打砖块

### [LeetCode 959 斜杠划分](https://leetcode-cn.com/problems/regions-cut-by-slashes/solution/you-xie-gang-hua-fen-qu-yu-by-leetcode-67xb/)



<img src="https://pic.leetcode-cn.com/1611302894-vmBtyK-image.png" width="300px" />

```c++
class Solution {
public:
    int h;
    int getIndex(int i,int j)
    {
        return (i*h+j);
    }
    int regionsBySlashes(vector<string>& grid)
    {
        h=grid.size();
        UF *uf=new UF(4*h*h);

        for(int i=0;i<=h-1;i++)
        {
            for(int j=0;j<=h-1;j++)
            {
                int index=getIndex(i,j);
                if(grid[i][j]=='/')
                {
                    uf->Union(index*4+0,index*4+3);
                    uf->Union(index*4+2,index*4+1);
                }
                else if(grid[i][j]=='\\')
                {
                    uf->Union(index*4+0,index*4+1);
                    uf->Union(index*4+2,index*4+3);
                }
                else
                {
                    uf->Union(index*4+0,index*4+1);
                    uf->Union(index*4+1,index*4+2);
                    uf->Union(index*4+2,index*4+3);
                }

                if(i<=h-2)
                    uf->Union(getIndex(i+1,j)*4,index*4+2);
                if(j<=h-2)
                    uf->Union(getIndex(i,j+1)*4+3,index*4+1);

            }
        }
        return uf->getSet();
    }
};
//leetcode submit region end(Prohibit modification and deletion)
```



