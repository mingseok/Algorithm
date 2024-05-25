## Array & Greedy

```java
class Solution {
    public int maxProfit(int[] prices) {
        int result = 0; // 이익을 저장할 변수, 초기값은 0 (아직 이익이 없음)

        // 배열을 처음부터 끝의 전 원소까지 반복, 마지막 요소는 비교 대상이 없으므로 포함하지 않음
        for (int i = 0; i < prices.length - 1; i++) {
            // 만약 다음 날의 가격(prices[i + 1])이 오늘의 가격(prices[i])보다 높다면,
            if (prices[i + 1] > prices[i]) {
                // 오늘 가격에 사서 내일 더 높은 가격에 팔아 이익을 얻는다
                result += prices[i + 1] - prices[i]; // 이익 누적
            }
        }
        return result; // 모든 가능한 이익을 더한 후, 최종 이익 반환
    }
}
```

<br/>
<br/>

```java
public class Main
{
	public static void main(String[] args) {
	    Scanner scan = new Scanner(System.in);
	    
	    // 조건 값들 입력 받기
	    int n = scan.nextInt();
	    int k = scan.nextInt();
	    int result = 0;
	 
	    while(true){
	        // 나머지를 더한 후 나누기
	        result += (n % k) + 1;
	        n /= k;
	        
	        // 나눌 수 없어지면 종료
	        if(n < k) break;
	    }
	    
	    //1이 될때까지 남은 값을 연산 횟수에 포함
	    result += (n - 1);
	    
	    System.out.println("result = " + result);  
	}
}
```
