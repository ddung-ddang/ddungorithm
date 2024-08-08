## LeetCode

- #### 819. Most Common Word

<br>

## Performance

- Time : 12 ms (81.87%)
- Memory : 42.4 MB (92.84%)

<br>

## Solution

```java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        String[] words = paragraph.toLowerCase().split("[!?',;.\s]+");
        Set<String> set = new HashSet<>();
        Map<String, Integer> map = new HashMap<>();

        for(String b : banned) {
            set.add(b);
        }

        for(String word : words) {
            if(set.contains(word)) {
                continue;
            }
            map.put(word, map.getOrDefault(word, 0) + 1);
        }

        String answer = "";
        int frequent = 0;

        for(String key : map.keySet()) {
            int value = map.get(key);
            if(value > frequent) {
                answer = key;
                frequent = value;
            }
        }

        return answer;
    }
}
```
