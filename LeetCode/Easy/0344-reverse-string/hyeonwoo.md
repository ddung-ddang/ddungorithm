## LeetCode


- #### 344. Reverse String

<br>

## Performance

- Time : 0 ms
- Memory : 45.6 MB

<br>

## Solution

```java
class Solution {

    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;
        char temp;

        while (left < right) {
            temp = s[left];
            s[left] = s[right];
            s[right] = temp;

            left++;
            right--;
        }
    }
}
```
