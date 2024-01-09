# 概念
其过程简要来说是对每一个可能的分支路径深入到不能再深入为止，而且每个节点只能访问一次.[百度](https://baike.baidu.com/item/%E6%B7%B1%E5%BA%A6%E4%BC%98%E5%85%88%E6%90%9C%E7%B4%A2/5224976)

# 实现思想
无向图通过转换为一个临界矩阵，其实就是遍历临界矩阵

![](./../../images/2-220H4153114520.gif)

如上图所示，先遍历v1,然后2和3随便，加入是2，现在4和5随机，如果是4，遍历8，接下来是5，然后递归结束依次返回，

最后返回到1，然后遍历3，6和7随便，如果是6，然后就是7，然后依次返回6，3，1，遍历完成

# 代码实现
```cpp
#include<iostream>
#include<climites>
#include<string>
using namespace std;
int N;
int map[100][100];//将图转换为临界矩阵，100这是为了简化，这样写不好，浪费空间
int visited[100];//查询是否已经遍历过
void CreateMap(){//建立邻接表
    int n;
    
    cin>>n;//现在输入连通
    for(int i = 0;i<n;i++){
        int p1,p2;
        cin>>p1>>p2;
        map[p1][p2] = 1;
        map[p2][p1] = 1;
    }
}

void DFS(int& n){
    if(visited[n]==0)cout<<n<<" ";//输出访问的节点
    visited[n]=1;
    for(int i = 1;i<N;i++){
        if(visited[i]==0&&map[n][i]==1){
            DFS(i);
        }
    }
}
void dfstraverse(){
    memset(visited,0,N+1);//初始化是否遍历
    for(int i = 1;i<=N;i++){
        if(visited[i]==0){
            DFS(i);
        }
    }
}
int main(){
    cin>>N;//输入图的节点个数
    CreateMap();
    dfstraverse();
}
/*
输入：
8
9
1 2
2 4
2 5
4 8
5 8
1 3
3 6
6 7
7 3
end:
1 2 4 8 5 3 6 7
 */
```


