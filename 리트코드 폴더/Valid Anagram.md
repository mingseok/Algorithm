## Valid Anagram

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        
        // 길이가 다르면 return
        if(s.length() != t.length())
            return false;
        
        // 알파벳 별 카운팅
        HashMap<Character, Integer> map = new HashMap<>();
        for(int i=0; i<s.length(); i++) {
            char key = s.charAt(i);
            map.put(key, map.containsKey(key) ? map.get(key)+1 : 0);
        }
        
        // 알파벳이 hashmap에 존재하지 않거나, 존재해도 개수가 다른 경우
        for(int i=0; i<t.length(); i++) {
            char key = t.charAt(i);
            if(!map.containsKey(key) || map.get(key) < 0)
                return false;
            else
                map.put(key, map.get(key)-1);
        }
        
        return true;
    }
}
```
<br/><br/>

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] sChar = s.toCharArray();
        char[] tChar = t.toCharArray();

        for (int temp : sChar) {
            sSum += temp;
        }

        for (int temp : tChar) {
            tSum += temp;
        }

        return sSum == tSum;
    }
}
```
