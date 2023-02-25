# C++刷题笔记

### Nothing is impossible!!!
> 1.从尾到头打印链表 
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
> 2.Spiral MAtrixII 数组
```
//利用左右上下设置边界，然后利用while依次向内塌陷；
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n,vector<int>(n,0));
        int left = 0;int right = n-1; int top = 0; int bottom = n-1;
        int count = 1;int tar = n * n;
        while(count <= tar) {
            for(int j = left;j <= right;j++) res[top][j] = count++;
            top++;
            for(int i = top;i <= bottom;i++) res[i][right] = count++;
            right--;
            for(int j = right;j >= left;j--) res[bottom][j] = count++;
            bottom--;
            for(int i = bottom;i >= top;i--) res[i][left] = count++;
            left++;
        }
        return res;
    }
};
```
> 移除链表元素
```
/**使用虚节点，统一头节点和其余节点；
 * Definition for singly-linked list.!
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 //链表定义：
 struct ListNode {
    int val;
    ListNOde *next;
    ListNode() : val(0),next(nullptr) {}
    ListNode(int x) : val(x),next(nullptr) {}
    ListNode(int x, ListNode *next) : val(int x) , next(next) {}
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* dummyHead = new ListNode(0);
        dummyHead -> next = head;
        ListNode* cur = dummyHead;
        while(cur -> next != NULL) {
            if(cur -> next -> val == val) {
                ListNode* tmp = cur -> next;
                cur -> next = cur -> next -> next;
                delete tmp;
            } else {
                cur = cur -> next;
            }
        }
        head = dummyHead -> next;
        delete dummyHead;
        return head;
    }
};
```
