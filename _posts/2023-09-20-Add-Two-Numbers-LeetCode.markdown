---
layout: post
title:  "Add Two Numbers! - LeetCode Solution - Explained!"
date:   2023-09-20 02:38:26 +0530
categories: LeetCode
tags: LeetCode, C#, LinkedList, Solution
---

Question:
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Solution
'''
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */
public class Solution {
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
        ListNode Result = new ListNode(0);
        ListNode p = l1, q = l2, curr = Result;
        int carry = 0;
        while (p != null || q != null){
            int x = (p != null) ? p.val : 0;
            int y = (q != null) ? q.val : 0;
            int sum = carry + x + y;
            carry = sum / 10;

            curr.next = new ListNode(sum%10);
            curr = curr.next;
            if (p != null) p = p.next;
            if (q != null) q = q.next;

        } 
        if (carry > 0){
            curr.next = new ListNode(carry);
        }
        return Result.next;    
    }
}
'''

Explaination

To solve this problem, we need to understand what a Linked List is.
A linked list is a linear data structure, in which the elements are stored in the form of a node. Each node contains two sub-elements. A data part that stores the value of the element and next part that stores the link to the next node

Constructor to Create a LinkedList would be : 
'''
public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
'''
That simply means each value has the pointer for the next value in the list.

Taking this into consideration, we do have two Linked List as input that is in reversed order and we need to find the sum of the Linked List.

Example:
l1 = [2, 4, 3]
l2 = [5, 6, 4]
sum= [7, 0, 4]

Now Consider The First element of l1 i.e l1.val = 2, l2.val=5 and sum would be l1.val + l2.val. Now loop this until both the list runs out of elements.

Breakdown:
'''
ListNode Result = new ListNode(0);
ListNode p = l1, q = l2, curr = Result;
int carry = 0;
'''
Result is a dummy node that serves as the head of the result linked list. It's initialized with a value of 0.
p and q are pointers initialized to the heads of the input linked lists l1 and l2, respectively.
curr is a pointer initially set to Result. It will be used to traverse and build the result linked list.
carry is initialized to 0. It keeps track of any carry generated during addition.

'''
while (p != null || q != null) {
'''
This while loop continues as long as either p or q is not null. It iterates through the linked lists, processing each digit.

'''
int x = (p != null) ? p.val : 0;
int y = (q != null) ? q.val : 0;
int sum = carry + x + y;
carry = sum / 10;
'''
x and y store the values of the current nodes p and q, respectively. If p or q is null, their value is considered as 0.
sum holds the sum of the current digits, plus any carry from the previous step.
carry is updated to hold the carry for the next iteration, which is calculated as the integer division of sum by 10.

'''
curr.next = new ListNode(sum % 10);
curr = curr.next;
if (p != null) p = p.next;
if (q != null) q = q.next;
'''

p and q pointers are moved to their respective next nodes if they are not null, effectively advancing through the input linked lists.
The loop continues processing each digit in the input linked lists until both p and q become null.


'''
return Result.next;
'''
Finally, the method returns Result.next, which is the head of the result linked list. 
