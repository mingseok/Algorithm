## Can Place Flowers

```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        if(flowerbed[0] ==0 && flowerbed.length ==1 )return true;
        int count= 0;
        int zeroCnt = 0;
        for(int i = 0 ;i < flowerbed.length ;i++){
            //count zero between 1
            if(flowerbed[i] == 0){
                if(i == 0 || i == flowerbed.length-1)//put 1 only if each side.
                    zeroCnt++;
                zeroCnt++;
            }else{
                count += (zeroCnt-1)/2;
                zeroCnt = 0;
            }
        }
        return count + (zeroCnt-1)/2 >= n;
    }
}
```
