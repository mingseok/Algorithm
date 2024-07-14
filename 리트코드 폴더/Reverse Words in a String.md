## Reverse Words in a String

```java
class Solution {
    public String reverseWords(String s) {
        
        String[] array = s.split(" ");
        StringBuilder result = new StringBuilder();
        
        for(String word : array) {
            StringBuilder sb = new StringBuilder(word);
            result.append(sb.reverse() + " ");
        }
        return result.toString().trim();
    }
}
```
