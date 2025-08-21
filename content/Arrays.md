# EASY

## Largest Element of the array:
Approaches: 

1. **Sort** and return the last element : O(n*logn)
2. **Traditional** for loop : O(n)
## Second Largest element of the array:
https://www.geeksforgeeks.org/problems/second-largest3735/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=second-largest
Approaches: 
1. **Sort** and return the second largest array (works only if no duplicates) : O(n*logn) 
2. Use **two for loops** where first one finds the largest, then second finds the second largest : O(2n)
3. Use two pointers, first will always point to the largest and second to second largest, return the second largest : O(n)
![[Pasted image 20250615212923.png]]

## Check if array is sorted:
https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/
Approaches: 
1. For each element we check if the previous one is smaller, if yes move to next element, else return false. O(n)
![[Pasted image 20250615213444.png]]
## Check if array is sorted and rotated:
https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/
Approaches:
1. Brute force: for each element rotate left and check if it is sorted until the end. O(n^2)
![[Pasted image 20250615213444.png]]
![[Pasted image 20250615213531.png]]

## Remove Duplicates from a sorted array:
https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/
Approaches: 
1. Use a **set** : O(n*log(n))+O(n)
	1. store all elements in a set, if they are duplicate, they will not be repeated
	2. Now put all elements of the set in the array from the starting of the array.
2. **Two pointers** : 
	1. Use i for 0th index, j for 1st index.
	2. if nums[i] != nums[j], then nums[i] = nums[j];
	3. increment.
	![[Pasted image 20250323222651.png]]

## Rotate array by K elements: 
https://leetcode.com/problems/rotate-array/description/
Approaches: 
1. Using a **temp array**: O(n)
	1. 1. Copy the last k elements into the temp array.
	2. Shift n-k elements from the beginning by k position to the right.
	3. Copy the elements into the main array from the temp array.
2. **Reversal Algorithm**: O(N), better space complexity.
	4. Reverse the last k elements of the array.
	5. Reverse the first n-k elements of the array.
	6. Reverse the whole array.
![[Pasted image 20250615214131.png]]
## Move Zeroes to the end:
https://leetcode.com/problems/move-zeroes/description/
Approaches:

1. Copy the non-zero elements, one by one in a **temp array**, then the remaining elements will be zero - O(2n)
2. Use **2 pointers** - O(n)
	1. pointer j will point to first zero, and i will point to the next index
	2. if nums[i] != 0, then swap nums[i] and nums[j]; i++; j++;
	3. else, i++;
![[Pasted image 20250615214658.png]]
## Linear Search
https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=who-will-win
Approaches:

1. Really?

## Union of Two Sorted Arrays
https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=union-of-two-sorted-arrays
Approaches:

1. Using Map - O((m+n)log(m+n))
2. Using Set - O((m+n)log(m+n)) 
3. Two Pointers - O(m+n) 
![[Pasted image 20250615215629.png]]
![[Pasted image 20250615215659.png]]

## Find the number that appears once, and the other numbers twice
https://leetcode.com/problems/single-number/description/

Approaches:
1.  Using a HashMap store all the elements(key) and their frequency(value), if value == 1, return that element.
2. XOR all elements
![[Pasted image 20250615215931.png]]
## Find the missing number in an array
https://leetcode.com/problems/missing-number/description/

Approaches:
1. Sort the array, then for each element check if the difference between the 2 consecutive elements is 1 or not : O(n*logn) + O(n)
2. Find the sum of first n elements using n(n+1)/2, then find the sum of the elements of array, the difference is the answer : O(n)
3. Find the XOR1 = XOR of first n elements, XOR2 = XOR of all the elements of the array, the final answer = XOR1^XOR2. : O(n) 
## Maximum Consecutive One's
https://leetcode.com/problems/max-consecutive-ones/description/

Approaches:
1. Use 2 variables, max_count and count (global and local max), Traverse through the array, once the count is more than max_count, update it, at 0 re-initialise count. O(n)
## Longest Subarray with given Sum K
https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=longest-sub-array-with-sum-k

Approaches: watch Striver video
https://www.youtube.com/watch?v=frf7qxiN2qU

1. Brute force: Generate all sub arrays, using 2 loops
	loop i : 0 to n
	loop j : i to n
	use these two loops to generate all the sub arrays, i.e. from i to j. Check if the sum == k, then take the max of current length and the old one.

 2. Use HashMap to store the <sum, index> where the sum is up to the index, if the prefix sum is x, then look for x-k in the HashMap and update the length accordingly.
	 ![[Pasted image 20240819141325.png]]

3.  Use 2 pointer, only for positives and zeroes, wont work for negative values.
# MEDIUM

## Two Sum
https://leetcode.com/problems/two-sum/description/

Approaches:
1. for every element, check all the next elements if their sum is equal to target: O(n^2).
2. Use Hashmap, add <nums[i], i> for each element in array, then check for the key, if it exists then return: O(n^2) but less than brute force.
![[Pasted image 20240802233240.png]]
3. Use 2 pointers, one left and one right : O(n) + O(n*logn) but you cannot return the indexes with this time complexity
	1. If nums[left]+nums[right] < target;
		1. left++
	2. if nums[left] + nums[right] > target;
		2. right--;
	3. else
		1. return "YES";
	Note: Sort first.

## Sort an array of 0s, 1s and 2s
https://leetcode.com/problems/sort-colors/description/

Approaches:
1. Count and put it in the same array: O(2*N)
2. use 3 pointers, low, mid, high: O(N)
![[Pasted image 20240804204118.png]]



## Find the Majority Element that occurs more than N/2 times
https://leetcode.com/problems/majority-element/description/

Approaches:
1. Use HashMap to store the <element, frequency> then return the element with frequency more than n/2 : O(n*logn) + O(n) {Reason: Insertion in Hashmap takes logn time and we do it for n times, second loop also takes n time}
2. Moore's Voting Algorithm: O(n)
![[Pasted image 20240806211040.png]]

## Maximum Subarray
https://leetcode.com/problems/maximum-subarray/description/
Approaches:

1. Brute force: Generate all sub arrays, use 2 loops
   i: 0 to n
   j: i to n
   check if sum is greater than global sum, if yes then replace
2. Kadane's Algorithm 
   ![[Pasted image 20240913170339.png]]
## Stock Buy and Sell
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/

Approaches:
1. Brute force: use two loops and calculate maxProfit from i to j for all
2. We can maintain a minimum from the start of the array and compare it with every element of the array, if it is greater than the minimum then take the difference and maintain it in max, otherwise update the minimum.
    ![[Pasted image 20250617163518.png]]

## Rearrange the array in alternating positive and negative items 
https://leetcode.com/problems/rearrange-array-elements-by-sign/description/

Approaches:
1. Take array of positives, negatives then merge one by one.
2. We know that the resultant array must start from a positive element so we initialize the positive index as 0 and negative index as 1 and start traversing the array such that whenever we see the first positive element, it occupies the space at 0 and then posIndex increases by 2 (alternate places).Similarly, when we encounter the first negative element, it occupies the position at index 1, and then each time we find a negative number, we put it on the negIndex and it increments by 2.
   ![[Pasted image 20250617175004.png]]

## Next Permutation
https://leetcode.com/problems/next-permutation/description/

1. Watch video

## Set Matrix Zeros
https://leetcode.com/problems/set-matrix-zeroes/

Approach: Note the row and column, and in the second iteration, make all 0 if row or column = 1
```
class Solution {
    public void setZeroes(int[][] matrix) {
        int n = matrix.length;
        int m = matrix[0].length;

        int[] rows = new int[n];
        int[] cols = new int[m];

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(matrix[i][j] == 0)
                {
                    rows[i] = 1;
                    cols[j] = 1;
                }
            }
        }

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(rows[i] == 1 || cols[j] == 1)
                    matrix[i][j] = 0;
            }
        }
    }
}
```

# HARD

## Pascal's Triangle
https://leetcode.com/problems/pascals-triangle/

WATCH THE VIDEO
```
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> ans = new ArrayList<>();

        for(int i=1;i<=numRows;i++)
        {
            List<Integer> st = new ArrayList<>();
            int a = 1;
            st.add(1);
            for(int j=1;j<i;j++)
            {
                a = a*(i-j);
                a = a/j;
                st.add(a);
            }
            ans.add(st);
        }

        return ans;
    }
}
```

## 