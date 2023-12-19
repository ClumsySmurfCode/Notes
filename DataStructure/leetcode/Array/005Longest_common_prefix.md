# 14 Longest Common Prefix

#### Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string "".

 

**Example 1:** </br>
`Input: strs = ["flower","flow","flight"]`</br>
`Output: "fl"`</br>

**Example 2:** </br>
`Input: strs = ["dog","racecar","car"]`</br>
`Output: ""`</br>
`Explanation: There is no common prefix among the input strings.`</br>
 

**Constraints:** </br>
`1 <= strs.length <= 200`</br>
`0 <= strs[i].length <= 200`</br>
`strs[i] consists of only lowercase English letters.`</br>



    class Solution {
          public String longestCommonPrefix(String[] strs) {
              /* 
              // Solution 1 
              StringBuilder ans = new StringBuilder();
              //If sort based on length we can have min and max string 
              //so that only one loop required.
              // if there is no matching in that case last one will not match with first 
              // so that we can return ""
              //  O(n log n)
              Arrays.sort(strs); 
              //Take first
              String first = strs[0];
              // take last 
              String last = strs[strs.length-1];
              // O(m)
              for(int i = 0; i<Math.min(first.length(),last.length()); i++ ){
                  if (first.charAt(i) != last.charAt(i)) {
                      return ans.toString();
                  }
                  ans.append(first.charAt(i));
              }
              //O(m*n log n)
              // O()
              return ans.toString();
          } */
          
          // Solution 2 
              if (strs == null || strs.length == 0) {
                  return "";
              }
              //take first string
              String prefix = strs[0];
              // start from 2nd string
              // O(n)
              //System.out.print(strs[2].indexOf("flo"));
              for (int i = 1; i < strs.length; i++) {
                  // check for all string if it return -1 then start cutting from last
                  // O(m)
                  // -1 if never occured and 0 if occured 
                  while (strs[i].indexOf(prefix) != 0) {
                      // do substring prefix
                      prefix = prefix.substring(0, prefix.length() - 1);
                      // if no char match then ""
                      if (prefix.isEmpty()) return "";                
                  }
              }
              return prefix;
          }    
      }
