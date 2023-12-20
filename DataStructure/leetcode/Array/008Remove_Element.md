## 27 Remove Element</br>
https://leetcode.com/problems/remove-element/description/ </br>

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.


> Example 1:</br>
`Input: nums = [3,2,2,3], val = 3`</br>
`Output: 2, nums = [2,2,_,_]`</br>

> Explanation: `Your function should return k = 2, with the first two elements of nums being 2.`</br>
`It does not matter what you leave beyond the returned k (hence they are underscores).`

> Example 2:</br>
`Input: nums = [0,1,2,2,3,0,4,2], val = 2`</br>
`Output: 5, nums = [0,1,4,0,3,_,_,_]`</br>

> Explanation: `Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.`
`Note that the five elements can be returned in any order.`</br>
`It does not matter what you leave beyond the returned k (hence they are underscores).`


Constraints:</br>
`0 <= nums.length <= 100`</br>
`0 <= nums[i] <= 50`</br>
`0 <= val <= 100`</br>
> [!NOTE]
> Time Complexcity : **O(n)**

     public int removeElement(int[] nums, int val) {
            int index = 0;
            for(int i = 0; i<nums.length; i++){
                if(nums[i]!=val){               
                    nums[index] = nums[i];    
                    index++;            
                }
            }
            return index;
        }
