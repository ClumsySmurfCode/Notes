> [!IMPORTANT]
> # 20. Valid Parentheses</br>
https://leetcode.com/problems/valid-parentheses/ </br>
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

`Example 1:`</br>
`Input: s = "()"`</br>
`Output: true`</br>

`Example 2:`</br>
`Input: s = "()[]{}"`</br>
`Output: true`

`Example 3:`</br>
`Input: s = "(]"`</br>
`Output: false`</br>
 

Constraints:
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.`</br>

      public boolean isValid(String s ) {
              //Souliton 1:  Via stack        
             /* Stack<Character> stack = new Stack<>();   
              //Null and zero
              if(s == null || s.length() ==0 ) return true;
              //Iterate 
              for (char c : s.toCharArray()) {
                  if (c == '(' || c == '{' || c == '[') {
                      stack.push(c);
                  } else if (c == ')' && !stack.isEmpty() && stack.peek() == '(') {
                      stack.pop();
                  } else if (c == '}' && !stack.isEmpty() && stack.peek() == '{') {
                      stack.pop();
                  } else if (c == ']' && !stack.isEmpty() && stack.peek() == '[') {
                      stack.pop();
                  } else {
                      return false;
                  }
              }
      
              return true;   */
              int openCount = 0;
      
              Stack<Character> stack = new Stack<>();
      
              for (char c : s.toCharArray()) {
                  if (c == '(' || c == '{' || c == '[') {
                      stack.push(c);
                  } else {
                      if (stack.isEmpty()) {
                          return false; // Closing bracket with no matching opening bracket
                      }
                      char top = stack.pop();
                      if ((c == ')' && top != '(') || 
                          (c == '}' && top != '{') || 
                          (c == ']' && top != '[')) {
                          return false; // Mismatched opening and closing brackets
                      }
                  }
              }
      
              return stack.isEmpty(); 
          }
