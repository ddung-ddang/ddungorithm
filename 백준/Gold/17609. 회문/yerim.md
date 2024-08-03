## 백준

- #### 17609. 회문

<br>

## Performance

- Time : 356 ms
- Memory : 34672 KB

<br>

## Solution

```java
import java.io.*;

public class Main {
    public static void main(String args[]) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int T = Integer.parseInt(br.readLine());

        for(int i = 0; i < T; i++) {
            String s = br.readLine();
            System.out.println(checkPalindrome(s.toCharArray()));
        }

        br.close();
    }

    private static int checkPalindrome(char[] s) {
        int len = s.length;
        int i = 0, j = len - 1;

        while(i < j) {
            if(s[i] == s[j]) {
                i++;
                j--;
            } else {
                int tmpI = i + 1, tmpJ = j;
                while(tmpI <= tmpJ && s[tmpI] == s[tmpJ]) {
                    tmpI++;
                    tmpJ--;
                }
                if(tmpI > tmpJ) {
                    return 1;
                }

                tmpI = i; tmpJ = j - 1;
                while(tmpI <= tmpJ && s[tmpI] == s[tmpJ]) {
                    tmpI++;
                    tmpJ--;
                }
                if(tmpI > tmpJ) {
                    return 1;
                }

                return 2;
            }
        }

        return 0;
    }
}
```


# Better Solution

- Time : 312 ms
- Memory : 34676 KB

<br>

```java
import java.io.*;

public class Main {
    public static void main(String args[]) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        
        int T = Integer.parseInt(br.readLine());

        for(int i = 0; i < T; i++) {
            String s = br.readLine();
            sb.append(checkPalindrome(s.toCharArray())).append('\n');
        }
        
        System.out.println(sb);

        br.close();
    }

    private static int checkPalindrome(char[] s) {
        int len = s.length;
        int i = 0;
        int j = len - 1;

        while(i < j) {
            if(s[i] == s[j]) {
                i++;
                j--;
                continue;
            } 
            
            // 유사회문인지 확인
            if(isSimilarPalindrome(s, i + 1, j) || isSimilarPalindrome(s, i, j - 1)) {
                return 1;
            }
            
            // 일반 문자열
            return 2;
        }

        return 0;
    }
    
    private static boolean isSimilarPalindrome(char[] s, int i, int j) {
        while(i <= j && s[i] == s[j]) {
            i++;
            j--;
        }
        
        return i > j;
    }
}
```

