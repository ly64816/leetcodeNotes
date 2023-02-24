# C语言
> 初始化git仓库
//算法题刷题笔记

class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        vector<int> A;
        while(head) {
            A.push_back(head->val);
            head = head->next;
        }
        reverse(A.begin(),A.end());
        return A;

    }
};
