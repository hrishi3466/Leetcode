28. Find the Index of the First Occurrence in a String

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
 
Example 1:

Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
Example 2:

Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
 

Constraints:

1 <= haystack.length, needle.length <= 104
haystack and needle consist of only lowercase English characters.

Solution:-

Using Two Pointer :-

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int n = needle.size();
        int h = haystack.size();

        int i = 0;
        int j = 0;

        if (n > h) {
            return -1;
        }

        while (i < h) {
            if (haystack[i] == needle[j]) {
                i++;
                j++;

                if (j == n) {
                    return i - n;
                }
            } else {
                i = i - j + 1;
                j = 0;
            }
        }

        return -1;
    }
};
```
Using substr() Fucntion:-
```cpp

class Solution {
public:
    int strStr(string haystack, string needle) {
        int n = needle.size();

        if( haystack.size() < needle.size()){
            return -1;
        }else{

        for(int i=0; i<haystack.size(); i++){
            if(haystack[i]==needle[0]){
                if(haystack.substr(i, n) == needle){
                    return i;
                }
            }
        }

        }

        return -1;

    }
};
```