## Next Greater Element
https://leetcode.com/problems/next-greater-element-i/

## Next Greater Element 2
https://leetcode.com/problems/next-greater-element-ii/description/

## Trapping Rainwater
https://leetcode.com/problems/trapping-rain-water/description/

Approaches:
1. For each element find leftMax and rightMax, the amount of water on the building is Min(leftMax, rightMax) - nums[i], find this of all buildings and sum it up. Calculate the arrays prefixSum and suffixSum to find the leftMax and rightMax.
   ![[Pasted image 20250615233952.png]]

## Sum of subarray minimum
https://leetcode.com/problems/sum-of-subarray-minimums/description/

Approaches:
1. Generate all the sub arrays, get the minimum element in each sub array, add it to the sum.
2. INCOMPLETE

## Asteroid Collision
https://leetcode.com/problems/asteroid-collision/

Approaches: 
1. If the steroid is positive, then push to the stack, if its negative then 
	1. while: stack top is positive and smaller than current negative element
		1. THEN pop from stack
	2. if: they are of same size
		1. THEN pop from stack
	3. if top is negative
		1. THEN push in the stack
   ![[Pasted image 20250618012431.png]]

## Remove k Digits
https://leetcode.com/problems/remove-k-digits/description/

Approaches:
1. WATCH THE VIDEO, DIDN'T UNDERSTAND THIS ONE PROPERLY 

## Largest rectangle in a histogram
https://leetcode.com/problems/largest-rectangle-in-histogram/description/

1. For each element, the area = height*(nse[i]-pse[i]-1). find max of all areas.
   ![[Pasted image 20250618015739.png]]
2. Watch video, and next time write this code.


## Maximal Rectangles
http://leetcode.com/problems/maximal-rectangle/description/

Approaches:
1. convert the matrix into histogram using prefix sum, then use largest rectangle in histogram to get the answer.
   ![[Pasted image 20250618025318.png]]

