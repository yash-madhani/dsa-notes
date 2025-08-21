
# EASY
## Remove Element
https://leetcode.com/problems/remove-element/

Approach: 2 pointers, both start from 0, if the current value is equal to 'val' then find the next value != val, and then replace. Try with pen paper if needed.
```
class Solution {
    public int removeElement(int[] nums, int val) {
        int n = nums.length;
        int j = 0;

        for(int i=0;i<n;i++) {
            if(nums[i] != val) {
                nums[j] = nums[i];
                j++;
            }
        }

        return j;
    }
}
```

## 

# MEDIUM

## Remove Duplicates from Sorted Array II
https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/

```
class Solution {
    public int removeDuplicates(int[] nums) {
        int k = 2;

        for(int i=2;i<nums.length;i++) {
            if(nums[k-2] != nums[i]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
    }
}
```

## 