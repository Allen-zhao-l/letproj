Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

##Example:
```
      Given nums = [2, 7, 11, 15], target = 9,

      Because nums[0] + nums[1] = 2 + 7 = 9,
      return [0, 1].
```
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> arraym;
        int index=0;
        for (auto &x :nums){
            arraym.insert(pair<int,int>(x,index));
            ++index;
        };
        for(int x=0;x<nums.size();++x){
            auto num=target-nums[x];
            if (arraym.find(num)!=arraym.end())
            {
                if (arraym[num]!=x)
                    return vector<int>{x,arraym[num]};
            }
        }
        return vector<int>();
    }
};
```
