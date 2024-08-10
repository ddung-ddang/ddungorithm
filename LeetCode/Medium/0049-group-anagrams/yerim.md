## LeetCode

- #### 49. Group Anagrams

<br>

## Performance

- Time : 7 ms (67.72%)
- Memory : 47.7 MB (65.66%)

<br>

## Solution

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for(String str : strs) {
            char[] arr = str.toCharArray();
            Arrays.sort(arr);
            String anagram = new String(arr);   // char 배열 -> String
            map.computeIfAbsent(anagram, key -> new ArrayList<>()).add(str);
        }
        
        List<List<String>> answer = new ArrayList<>();
        
        for(String key : map.keySet()) {
            answer.add(map.get(key));
        }
        
        return answer;
    }
}
```