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
		        if (s.length() != t.length()) {
		            return false;
		        }
		        int[] alph = new int[26]; 
		        int[] alph2 = new int[26];
	       
		        for (int i = 0; i < s.length(); i++) {
		            char sArray = s.charAt(i);
		            char tArray = t.charAt(i);
		            alph[sArray-97]++;            
		            alph2[tArray-97]++; 
		        }
		        for (int i = 0; i < alph.length; i++) {
		            if (alph[i] != alph2[i]) {
		                return false;
		            }
		        }
		        return true;
		    }
```
