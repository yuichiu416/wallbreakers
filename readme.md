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

[867. Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)
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

```ruby
def transpose(a)
    return a if a.nil? || a.length < 1 || a[0].length < 1
    ans = Array.new(a[0].length) {Array.new(a.length)}
    for i in 0...a.length
        for j in 0...a[0].length
            ans[j][i] = a[i][j]
        end
    end
    ans
end
```

[832. Flipping an Image](https://leetcode.com/problems/flipping-an-image/)
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] A) {
        if(A == null || A.length < 1 || A[0].length < 1){
            return A;
        }
        for(int i = 0; i < A.length; i++){
            flip(A[i]);
            invert(A[i]);
        }
        return A;
    }
    private void flip(int[] row){
        int left = 0, right = row.length - 1;
        while(left < right){
            int temp = row[left];
            row[left++] = row[right];
            row[right--] = temp;
        }
        
    }
    private void invert(int[] row){
        for(int i = 0; i < row.length; i++){
            if(row[i] == 1){
                row[i] = 0;
            } else{
                row[i] = 1;
            }
        }
    }
}

```ruby
def flip_and_invert_image(a)
    return a if a.nil? || a.empty? || a[0].empty?
    a.each.with_index{ |row, i| a[i] = row.reverse.map { |ele| ele == 1 ? 0:1 }}
end
```

[412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)
```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> ans = new ArrayList();
        for(int i = 1; i <= n; i++){
            if(i % 3 == 0 && i % 5 == 0){
                ans.add("FizzBuzz");
            } else if(i % 3 == 0){
                ans.add("Fizz");
            } else if(i % 5 == 0){
                ans.add("Buzz");
            } else{
                ans.add(String.valueOf(i));
            }
        }
        return ans;
    }
}
```

```ruby
def fizz_buzz(n)
    ans = []
    for i in 1..n
        if i % 3 == 0 && i % 5 == 0
            ans << "FizzBuzz"
        elsif i % 3 == 0
            ans << "Fizz"
        elsif i % 5 == 0
            ans << "Buzz"
        else
            ans << i.to_s
        end
    end
    ans
end
```

[66. Plus One](https://leetcode.com/problems/plus-one/)
```java
class Solution {
    public int[] plusOne(int[] nums) {
        for(int i = nums.length - 1; i >= 0; i--){
            if(nums[i] == 9) {
                nums[i] = 0;
            }
            else {
                nums[i] += 1;
                return nums;
            }
        }
        if(nums[0] == 0){
            int[] result = new int[nums.length + 1];
            result[0] = 1;
            return result;
        }

        return new int[0];
    }
}
```