> [!TIP]
> > ##  21. Merge Two Sorted Lists

***You are given the heads of two sorted linked lists list1 and list2. Merge the two lists into one sorted list. </br>
The list should be made by splicing together the nodes of the first two lists. </br>
Return the head of the merged linked list.*** </br>



Example 1:</br>
`Input: list1 = [1,2,4], list2 = [1,3,4]`</br>
`Output: [1,1,2,3,4,4]`</br>

Example 2:</br>
`Input: list1 = [], list2 = []`</br>
`Output: []`</br>

Example 3:</br>
`Input: list1 = [], list2 = [0]`</br>
`Output: [0]`</br>
 

Constraints:</br>
`The number of nodes in both lists is in the range [0, 50].`</br>
`-100 <= Node.val <= 100`</br>
`Both list1 and list2 are sorted in non-decreasing order.`</br>
> [!NOTE]
> O(M+N)

    /**
     * Definition for singly-linked list.
     * public class ListNode {
     *     int val;
     *     ListNode next;
     *     ListNode() {}
     *     ListNode(int val) { this.val = val; }
     *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
     * }
     */

       public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
              if (list1!=null && list2!=null) {
                  if(list1.val<list2.val){
                      list1.next = mergeTwoLists(list1.next,list2);
                      return list1;
                  }else{
                      list2.next = mergeTwoLists(list1,list2.next);
                      return list2;
                  }
              }
              // if List1 reached to end
              if(list1==null)
                  return list2;  
              //if equal       
              return list1;
          }
