You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

##Example

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *pl=new ListNode(0),*end=pl;
        int u=0;
        while (l1!=nullptr | l2!=nullptr | u!=0){
            int v1=0,v2=0;
            if (l1!=nullptr){
                v1=l1->val;
                l1=l1->next;
            }
            if (l2!=nullptr){
                v2=l2->val;
                l2=l2->next;
            }
            v1=v1+v2+u;
            u=v1/10;
            end->next=new ListNode(v1%10);
            end=end->next;
        }
        return pl->next;
    }
};
```
