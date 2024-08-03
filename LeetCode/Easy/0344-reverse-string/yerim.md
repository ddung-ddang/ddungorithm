## LeetCode

- #### 344. Reverse String

<br>

## Performance

- Time : 0 ms (100.00%)
- Memory : 45.7 MB (70.98%)

<br>

## Solution

```java
class Solution {
    public void reverseString(char[] s) {
        int len = s.length;
        int start = 0;
        int end = len - 1;

        while(start < end) {
            char tmp = s[start];    // Java는 swap 함수 존재하지 않음
            s[start] = s[end];
            s[end] = tmp;

            start++;
            end--;
        }

    }
}
```
