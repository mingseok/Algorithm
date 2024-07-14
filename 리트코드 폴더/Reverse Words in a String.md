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

<br/><br/>

```java
class Solution {
  public String reverseWords(String s) {
    char[] charArray = s.toCharArray();
    int start = 0;
    int end = 0;
    while (end < charArray.length) {
      if (charArray[end] == ' ') {
        this.reverse(charArray, start, end - 1);
        start = end + 1;
      }
      end++;
    }
    this.reverse(charArray, start, end - 1);
    return new String(charArray);
  }

  private void reverse(char[] charArray, int start, int end) {
    while (start < end) {
      char temp = charArray[start];
      charArray[start++] = charArray[end];
      charArray[end--] = temp;
    }
  }
}
```
