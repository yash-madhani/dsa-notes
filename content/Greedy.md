
## Valid Parenthesis Checker
https://leetcode.com/problems/valid-parenthesis-string/description/

Approaches: 
1. Explore all possible combinations using recursion, TC = O(3^N)
   ![[Pasted image 20250628013500.png]]
2. Maintain a range of min and max
   ![[Pasted image 20250628021315.png]]

## Jump Game
https://leetcode.com/problems/jump-game/description/

Approaches:
1. Use a maxIndex variable
   ![[Pasted image 20250628021500.png]]

## Jump Game II
https://leetcode.com/problems/jump-game-ii/description/

Approaches:
1. Use recursion to explore all possible options
2. Use a range of left and right to get the number of jumps, WATCH THE VIDEO
   ![[Pasted image 20250628212458.png]]
## Candy
https://leetcode.com/problems/candy/description/

Approaches:
1. Give candies considering on the left neighbor, then only the right neighbor and then take the max of both.
   ![[Pasted image 20250629020058.png]]
2. You can optimize TC of O(2N) and SC of O(N). WATCH THE VIDEO FOR THE SAME.
3. Third method uses slope concept, WATCH THE VIDEO FOR THE SAME.
## Question

