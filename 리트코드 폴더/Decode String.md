## Decode String

```java
class Solution {
    public String decodeString(String s) {
        Deque<Integer> st = new ArrayDeque<>();
        Deque<StringBuilder> st1 = new ArrayDeque<>();
        StringBuilder sb = new StringBuilder();
        int n = 0;

        for (char c : s.toCharArray()) {
            if (Character.isDigit(c)) {
                n = n * 10 + (c - '0');
            } else if (c == '[') {
                st.push(n);
                n = 0; 
                st1.push(sb);
                sb = new StringBuilder();
            } else if (c == ']') {
                int k = st.pop();
                StringBuilder temp = sb;
                sb = st1.pop();
                while (k-- > 0) {
                    sb.append(temp);
                }
            } else {
                sb.append(c);
            }
        }
        return sb.toString();
    }
}
```


<br/><br/>

```java
class Solution {
    int i = 0;

    public String decodeString(String s) {
        int cnt = 0;    
        StringBuilder sb = new StringBuilder();

        while (i < s.length()) {
            char c = s.charAt(i++);

            if (Character.isDigit(c)) {
                cnt = (cnt * 10) + Character.getNumericValue(c);
            } else if (c == '[') {
                String inner = decodeString(s);

                for (int i = 0; i < cnt; i++) {
                    sb.append(inner);
                }
                cnt = 0;
            } else if (c == ']') {
                break;
            } else {
                sb.append(c);
            }
        }

        return sb.toString();
    }
}
```
