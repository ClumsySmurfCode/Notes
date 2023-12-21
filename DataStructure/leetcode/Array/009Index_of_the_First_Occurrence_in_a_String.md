# 28. Find the Index of the First Occurrence in a String
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

 

Example 1:</br>
`Input: haystack = "sadbutsad", needle = "sad"`</br>
`Output: 0`</br>
`Explanation: "sad" occurs at index 0 and 6.`</br>
`The first occurrence is at index 0, so we return 0.`</br>

Example 2:</br>
`Input: haystack = "leetcode", needle = "leeto"`</br>
`Output: -1`</br>
`Explanation: `"leeto" did not occur in "leetcode", so we return -1.`</br>
 

Constraints:</br>
`1 <= haystack.length, needle.length <= 104`</br>
`haystack and needle consist of only lowercase English characters.`</br>

      public int strStr(String haystack, String needle) {
              int haylength = haystack.length();
              int needlelength = needle.length();       
              if (haylength < needlelength)
                  return -1;
              //sadbutsad
              //System.out.println(haystack.length()); 
              //sadbut
              //System.out.print(haystack.length()-needle.length());
              // Can reduce to avoid 2nd occurence ->  for (int i=0;i<=haystack.length()-needle.length();i++)
              // m(n-m)
              for (int i=0;i<=haystack.length()-needle.length();i++) {  
                  int nIndex = 0; // sad          
                  while (nIndex<needlelength && haystack.charAt(i+nIndex)==needle.charAt(nIndex)) {
                      nIndex++; 
                  }
                  if (nIndex == needlelength) return i;
              }
              return -1;
          }

> [!IMPORTANT]
> Time Complexity
1. The outer loop iterates from 0 to (n - m), where n is the length of haystack and m is the length of needle. This gives us **O(n - m)** iterations.
2. Inside the outer loop, there is a while loop that iterates up to m times, where m is the length of needle. In the worst case, the while loop iterates m times for each iteration of the outer loop.
3. Therefore, the total number of iterations of the while loop across all iterations of the outer loop is **O((n - m) * m)**.
4. Since each iteration of the while loop consists of constant-time operations (such as character comparisons), the overall time complexity is **O((n - m) * m)**.
5. This time complexity arises because for each potential starting position of the needle within the haystack, the algorithm needs to compare at most m characters to determine if there is a match. The outer loop runs (n - m + 1) times to cover all possible substrings of haystack of length needle. Therefore, the overall time complexity is **O((n - m) * m)**.
