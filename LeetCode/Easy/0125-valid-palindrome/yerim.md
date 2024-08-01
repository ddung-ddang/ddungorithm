## LeetCode

- #### 125. Valid Palindrome

<br>

## Performance

- Time : 13 ms (40.76%)
- Memory : 44.7 MB (37.72%)

<br>

## Solution

```java
class Solution {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase().replaceAll("[^a-z0-9]+", "");

        int i = 0;
        int len = s.length();

        while(i < len / 2) {
            if(s.charAt(i) != s.charAt(len - i - 1)) {
                return false;
            }
            i++;
        }

        return true;
    }
}
```
