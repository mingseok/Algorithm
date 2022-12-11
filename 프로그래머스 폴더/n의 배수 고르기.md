## n의 배수 고르기

```java
class Solution {
    public int[] solution(int n, int[] numlist) {
        
        List<Object> arrayList = new ArrayList<>();
        for (int i = 0; i < numlist.length; i++) {
            if (numlist[i] % n == 0) {
                arrayList.add(numlist[i]);
            }
        }

        int[] answer = new int[arrayList.size()];
        for (int i = 0; i < arrayList.size(); i++) {
            answer[i] = (int) arrayList.get(i);
        }

        return answer;
    }
}
```