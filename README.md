# C++刷题笔记

### 2.24
> 从尾到头打印链表
```

//解法一，传到vector，利用std的reverse暴力反转
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
//解法二，利用cur，temp，pre把链表反转后输出；
class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        ListNode* pre,*temp,*cur;
        cur = head;
        pre = NULL;
        while(cur) {
            temp = cur -> next;
            cur -> next = pre;
            pre = cur;
            cur = temp;
        }
        vector <int> A;
        while(pre) {
            A.push_back(pre ->val);
            pre = pre -> next;
        }
        return A;
    }
};
```
