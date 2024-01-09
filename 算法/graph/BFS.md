---
title: BFS
date: 2022-10-29 22:32:30
tags: 算法
---
# 概念：
![二叉树](https://pic.leetcode-cn.com/4d908dab4fe456418f3c06a124c4a0391c67f19780bfafc24d33878541faa665-image.png)
什么是BFS?

BFS全称Breadth first search(广度优先遍历)

采用遍历树，按层遍历，辅助一个队列，用来存当前层级的节点
# 时间
$O(n)$
# 代码实现

遍历树
```cpp
class demo{
    public:
    void bfs(TreeNode* root){
        if(root==nullptr){
            return;
        }
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()){
            int size = q.size();
            for(int i  = 0;i<size;i++){
                TreeNode* node = q.front();
                q.pop();
                //遍历
                if(node->left!=nullptr){
                    q.push(node->left);
                }
                if(node->right!=nullptr){
                    q.push(node->right);
                }
            }
        }
    }
};
```