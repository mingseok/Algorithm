## Backspace String Compare

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        int i = s.length() - 1;
        int j = t.length() - 1;

        while (i >= 0 || j >= 0) {
            i = getNextValidCharIndex(s, i);
            j = getNextValidCharIndex(t, j);

            if (i >= 0 && j >= 0 && s.charAt(i) != t.charAt(j)) {
                return false;
            }
            if ((i >= 0) != (j >= 0)) {
                return false;
            }
            i--;
            j--;
        }

        return true;
    }

    private int getNextValidCharIndex(String str, int index) {
        int skip = 0;
        while (index >= 0) {
            if (str.charAt(index) == '#') {
                skip++;
            } else if (skip > 0) {
                skip--;
            } else {
                break;
            }
            index--;
        }
        return index;
    }
}
```
