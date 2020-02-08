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
```ruby
def sort_array_by_parity(a)
    return a if a.nil? || a.length <= 1
    left, right = 0, a.length - 1
    while left < right
        while left < right && a[left].even?
            left += 1 
        end 
        break if left >= right
        while left < right && a[right].odd?
            right -= 1 
        end
    
        break if left >= right
        a[left], a[right] = a[right], a[left]
        left += 1
        right -= 1
    end
    a
end
```

[]()
```java
class Solution {
    public int[][] transpose(int[][] A) {
        if(A == null || A.length < 1 || A[0].length < 1){
            return A;
        }
        int[][] ans = new int[A[0].length][A.length];
        for(int i = 0; i < A.length; i++){
            for(int j = 0; j < A[i].length; j++){
                ans[j][i] = A[i][j];
            }
        }
        return ans;
    }
}
```
