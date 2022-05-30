# RotateLinkedlist
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if(head==nullptr || head->next==nullptr) return head;
        ListNode* tmp = head;
        int len = 1;
        while(tmp->next){
            len++;
            tmp = tmp->next;
        }
        if(k%len==0) return head;
        tmp->next = head;
        tmp = head;
        for(int i=0;i<len-(k%len)-1;i++){
            tmp = tmp->next;
        }
        head = tmp->next;
        tmp->next = nullptr;
        return head;
    }
};
