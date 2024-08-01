## LeetCode


- #### 125. Valid Palindrome

<br>

## Performance

- Time : 254 ms
    - LeetCode 특성 상 Kotlin 빌드 타임이 포함됨
- Memory : 38.5 MB

<br>

## Solution

```kt
class Solution {

    private val regex: Regex = Regex("[^a-z0-9]")

    fun isPalindrome(s: String): Boolean {
        val preprocessed: String = preprocess(s)
        val length: Int = preprocessed.length
        val mid: Int = length ushr 1

        for (i in 0 until mid) {
            if (preprocessed[i] != preprocessed[length - i - 1]) {
                return false
            }
        }

        return true
    }

    private fun preprocess(s: String): String {
        return s.lowercase()
            .replace(regex, "")
    }
}
```
