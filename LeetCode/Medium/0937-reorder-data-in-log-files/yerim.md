## LeetCode

- #### 937. Reorder Data in Log Files

<br>

## Performance

- Time : 4 ms (75.82%)
- Memory : 44.6 MB (60.82%)

<br>

## Solution

```java
class Solution {
    public String[] reorderLogFiles(String[] logs) {
        List<String> digits = new ArrayList<>();
        List<String> letters = new ArrayList<>();

        for(String log : logs) {
            String[] s = log.split(" ", 2); // 공백을 기준으로 2개의 문자열로 분리

            if(Character.isLetter(s[1].charAt(0))) {
                letters.add(log);
            } else {
                digits.add(log);
            }
        }

        Collections.sort(letters, (o1, o2) -> {
            String[] l1 = o1.split(" ", 2);
            String[] l2 = o2.split(" ", 2);

            if(l1[1].equals(l2[1])) {
                return l1[0].compareTo(l2[0]);
            }
            return l1[1].compareTo(l2[1]);
        });

        List<String> answer = new ArrayList<>();
        answer.addAll(letters);
        answer.addAll(digits);

        return answer.toArray(new String[answer.size()]);   // List -> Array로 변환
    }

}
```
