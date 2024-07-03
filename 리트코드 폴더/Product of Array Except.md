## Product of Array Except

```java
class Solution {
    public int[]  productExceptSelf(int[] nums) {
        int left = 1;
        int right = 1;
        int[] result = new int[nums.length];

        for (int idx = 0; idx < nums.length; idx++) {
            result[idx] = left;
            left *= nums[idx];
        }


        for (int idx = nums.length - 1; idx >= 0; idx--) {
            result[idx] *= right;
            right *= nums[idx];
        }

        return result;
    }
}
```

<br/><br/>

```java
public class Main {
	public static void main(String[] args) {
	    Scanner scan = new Scanner(System.in);
	    
	    int n = scan.nextInt();
	    int k = scan.nextInt();
	    int result = 0;
	 
	    while(true){
	        result += (n % k) + 1;
	        n /= k;
	        if(n < k) break;
	    }
	    result += (n - 1);
	    System.out.println("result = " + result);  
	}
}
```
