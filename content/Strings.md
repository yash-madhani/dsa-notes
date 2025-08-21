# Basic and Easy String Problems

## Reverse Words in a String
https://leetcode.com/problems/reverse-words-in-a-string/description/

Split and append in reverse order
```
class Solution {
    public String reverseWords(String s) {
        String[] arr = s.trim().split("\\s+");
        StringBuilder sb = new StringBuilder();

        for(int i = arr.length-1;i>=0;i--)
        {
            sb.append(arr[i]);
            if(i != 0)
                sb.append(" ");
        }

        return sb.toString();
    }
}
```

## Largest Odd Number in String
https://leetcode.com/problems/largest-odd-number-in-string/description/

Find the first odd number from the back and return upto that point.
```
class Solution {
    public String largestOddNumber(String num) {
        for(int i=num.length()-1;i>=0;i--)
        {
            if(num.charAt(i)%2 == 1)
            {
                return num.substring(0,i+1);
            }
        }
        return "";
    }
}
```

## Longest Common Prefix
https://leetcode.com/problems/longest-common-prefix/description/

Sort in dictionary order and compare first and last element.
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        Arrays.sort(strs);
        String s1 = new String(strs[0]);
        String s2 = new String(strs[strs.length - 1]);
        StringBuilder sb = new StringBuilder("");
        for(int i=0;i<Math.min(s1.length(),s2.length());i++)
        {
            if(s1.charAt(i) == s2.charAt(i))
                sb.append(s1.charAt(i));
            else
                break;
        }
        return sb.toString();
    }
}
```

## Isomorphic String
https://leetcode.com/problems/isomorphic-strings/description/

```

```