349. Intersection of Two Arrays

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

 

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
 

Constraints:

1 <= nums1.length, nums2.length <= 1000
0 <= nums1[i], nums2[i] <= 1000

Solution:-

My Approach 
```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {

        set<int>ans;
        

        for(int i=0; i< nums1.size(); i++){
            for(int j=0; j<nums2.size(); j++){
                if( nums1[i]==nums2[j]){
                    ans.insert(nums1[i]);
                    break;
                }
            }
        }

       return  vector<int>(ans.begin(), ans.end());


        
    }
};

```
Using unordered_set & count method 

```cpp

class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {

        unordered_set<int> s(nums1.begin(), nums1.end());
        unordered_set<int> result;
        for (auto c : nums2) {
            if (s.count(c)) {
                result.insert(c);
            }
        }

        return vector<int>(result.begin(), result.end());
    }
};

```
Sorting & Two Pointer 

```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {

        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());

        vector<int> result;

        int i=0,j=0;

        while( i< nums1.size() && j<nums2.size()){

            
            if( nums1[i] == nums2[j]){
                 if(result.empty() || result.back() != nums1[i] ){
                     result.push_back(nums1[i]);

                 }
                i++;
                j++;
            }
            else if( nums1[i]<nums2[j]){
                i++;
            }
            else{
                j++;
            }
        }

        return result ;
    }
};
```




