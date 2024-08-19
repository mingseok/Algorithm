

```java
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.stream.Collectors;

class Solution {
    public String predictPartyVictory(String senate) {
        Deque<Character> deque = senate.chars()
                .mapToObj(c -> (char) c)
                .collect(Collectors.toCollection(ArrayDeque::new));

        int radiantBanCount = 0;
        int direBanCount = 0;
        while (radiantBanCount != deque.size() && direBanCount != deque.size()) {
            Character c = deque.removeFirst();
            if (c == 'R') {
                if (direBanCount == 0) {
                    deque.addLast(c);
                    radiantBanCount++;
                } else {
                    direBanCount--;
                }
            } else {
                if (radiantBanCount == 0) {
                    deque.addLast(c);
                    direBanCount++;
                } else {
                    radiantBanCount--;
                }
            }
        }

        return (radiantBanCount > direBanCount) ? "Radiant" : "Dire";
    }
}
```

<br/><br/>

```java
class Solution {
    fun predictPartyVictory(senate: String): String {
        
        val vote = BooleanArray(senate.length) { false }
        
        var rCount = 0
        var dCount = 0
        
        while(rCount < senate.length && dCount < senate.length) {
            
            for(i in 0 until senate.length) {
                if(vote[i]) continue
                if(rCount == senate.length || dCount == senate.length) break
                
                if(senate[i] == 'R') {
                    if(rCount < dCount) vote[i] = true
                    rCount += 1
                }else {
                    if(dCount < rCount) vote[i] = true
                    dCount += 1
                }
            }
            
        }
        
        return if(rCount == senate.length) "Radiant" else "Dire"
        
    }
}
```
