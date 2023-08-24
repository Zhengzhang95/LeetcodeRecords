```c++
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        // 边界判断
        if (head == NULL || head->next == NULL) return NULL;
        // 定义快慢指针
        ListNode* slowHead = head;
        ListNode* fastHead = head;

        while (fastHead->next != NULL && fastHead->next->next != NULL) {
            slowHead = slowHead->next;
            fastHead = fastHead->next->next;
            // 快慢指针相遇
            if (fastHead == slowHead) {
                ListNode* indexHead1 = slowHead;
                ListNode* indexHead2 = head;
                while (indexHead1 != indexHead2) {
                    indexHead1 = indexHead1->next;
                    indexHead2 = indexHead2->next;
                }
                return indexHead2;
            }
        }
        return NULL;
    }
};

```
