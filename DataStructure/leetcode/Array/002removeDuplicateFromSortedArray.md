## Remove Duplicate from sorted array - 26

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.
Custom Judge:

The judge will test your solution with the following code:

>int[] nums = [...]; // Input array
>int[] expectedNums = [...]; // The expected answer with correct length

>int k = removeDuplicates(nums); // Calls your implementation

      assert k == expectedNums.length;
      for (int i = 0; i < k; i++) {
          assert nums[i] == expectedNums[i];
      }
If all assertions pass, then your solution will be accepted.

 

`Example 1:`</br>
`Input: nums = [1,1,2]`</br>
`Output: 2, nums = [1,2,_]`</br>
`Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.`
`It does not matter what you leave beyond the returned k (hence they are underscores).`

`Example 2:`</br>
`Input: nums = [0,0,1,1,1,2,2,3,3,4]`</br>
`Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]`</br>
`Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.`
`It does not matter what you leave beyond the returned k (hence they are underscores).`
 

Constraints:</br>
`1 <= nums.length <= 3 * 104`</br>
`-100 <= nums[i] <= 100`</br>
`nums is sorted in non-decreasing order.`</br>

            class Solution {
                public int removeDuplicates(int[] nums) {
                    /*Map<Integer,Integer> map = new HashMap<>();
                    int k = 0;
                    for(int i = 0; i<nums.length;i++){
                       if(map.containsKey(nums[i])){
                            map.put(nums[i],i);
                            k++;
                       }
                      
                    }
                    return k;*/
                    int j = 1;
                    for (int i = 1; i < nums.length; i++) {
                        if (nums[i] != nums[i - 1]) {
                            nums[j] = nums[i];
                            j++;
                        }
                    }
                    return j;
                    /*
                    0 1 2 3 4
                    */
                }
            }
