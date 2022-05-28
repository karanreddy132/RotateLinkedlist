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
        if(head==nullptr) return head;
        int len = 1;
        ListNode* tmp = head;
        while(tmp->next){
            len++;
            tmp = tmp->next;
        }
        
        if(k%len==0) return head;
        if(tmp!=head)
            tmp->next = head;
        
        tmp = head;
        int length = len;
        while(length-1>k%len){
            tmp = tmp->next;
            length--;
        }

        head = tmp->next;
        tmp->next = nullptr;
        
         return head;
    }
};
