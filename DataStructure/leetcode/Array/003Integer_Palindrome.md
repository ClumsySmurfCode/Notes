# Integer palindrome - 9 
#### Given an integer x, return true if x is a palindrome, and false otherwise. 

`Example 1:`</br>
`Input: x = 121`</br>
`Output: true`</br>
`Explanation: 121 reads as 121 from left to right and from right to left.`</br>

`Example 2:`</br>
`Input: x = -121`</br>
`Output: false`</br>
`Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.`</br>

`Example 3:`</br>
`Input: x = 10`</br>
`Output: false`</br>
`Explanation: Reads 01 from right to left. Therefore it is not a palindrome.`</br>


        public boolean isPalindrome(int x) {
                int intial = x;
                int reverse = 0;
                if(intial < 0) return false;
                while (x != 0) {
                   int digit = x % 10;  // Get the last digit of temp
                   reverse = reverse * 10 + digit;  // Append the digit to reverse
                   x = x/10;   // Remove the last digit from temp
                }
                return intial == reverse? true : false;
            }
