[905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)
```java
class Solution {
    public int[] sortArrayByParity(int[] A) {
        if(A == null || A.length <= 1) {
            return A;
        }
        int left = 0, right = A.length - 1;
        while(left < right){
            while(left < right && A[left] % 2 == 0){
                left++;
            }
            if(left >= right){
                break;
            }
            while(left < right && A[right] % 2 != 0){
                right--;
            }
            if(left >= right){
                break;
            }
            swap(A, left++, right--);
        }
        return A;
    }
    private void swap(int[] A, int left, int right){
        int temp = A[left];
        A[left] = A[right];
        A[right] = temp;
    }
}
```
