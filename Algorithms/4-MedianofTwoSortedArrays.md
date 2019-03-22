Median of Two Sorted Arrays

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

##Example1:
nums1 = [1, 3]
nums2 = [2]

The median is 2.0

##Example2:
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5

```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int> &nums1, vector<int> &nums2) {

        int i = 0, j = 0, k = 0;
        vector<int> sums;
        double x = 0;
        unsigned long y, z;
        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i]<nums2[j]){
                sums.push_back(nums1[i]);
                ++i;
            } else{
                sums.push_back(nums2[j]);
                ++j;
            }
        }
        while (i<nums1.size())
        {
            sums.push_back(nums1[i]);
            ++i;
        }
        while (j<nums2.size())
        {
            sums.push_back(nums2[j]);
            ++j;
        }
        i = sums.size() % 2;
        k = sums.size() / 2;
        if (i == 0) {
            x = (sums[k-1] + sums[k]) / 2.0;
        } else {
            x = sums[k];
        }
        return x;
    }
};
```
