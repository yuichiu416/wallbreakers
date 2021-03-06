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

```ruby
def plus_one(digits)
    (digits.join("").to_i + 1).to_s.split("").map(&:to_i)
end
```

[171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)

```java
class Solution {
    public int titleToNumber(String s) {
        String map = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        int sum = 0;
        int level = 1;
        for(int i = s.length() - 1; i >= 0; i--){
            char c = s.charAt(i);
            int val = (map.indexOf(c) + 1) * level;
            sum  += val;
            level *= 26;
        }
        return sum;
    }
}
```

[171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)

```java
class Solution {
    public int titleToNumber(String s) {
        if(s == null || s.length() < 1){
            return 0;
        }
        String letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        int sum = 0, multiply = 1;
        for(int i = s.length() - 1; i >= 0; i--){
            int index = letters.indexOf(s.charAt(i));
            int val = (index + 1) * multiply;
            sum += val;
            multiply *= 26;
        }
        return sum;
    }
}
```

```ruby
def title_to_number(s)
    return 0 if s.nil? || s.length == 0
    sum, multiply = 0, 1
    letters = ("A".."Z").to_a
    (s.length - 1).downto(0) do |i|
        index = letters.index(s[i])
        sum += (index + 1) * multiply
        multiply *= 26
    end
    sum
end
```

[231. Power of Two](https://leetcode.com/problems/power-of-two/)

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if(n <= 0){
            return false;
        }
        while(n > 1){
            if(n % 2 != 0){
                return false;
            } else{
                n /= 2;
            }
        }
        return true;
    }
}
```

```ruby
def is_power_of_two(n)
    return false if n <= 0
    while n > 1
        if n.odd?
            return false
        else
            n /= 2
        end
    end
    true
end
```


[344. Reverse String](https://leetcode.com/problems/reverse-string/)

```java
class Solution {
    public void reverseString(char[] s) {
        if(s == null || s.length < 1){
            return;
        }
        int l = 0, r = s.length - 1;
        while(l < r){
            swap(s, l++, r--);
        }
    }
    private void swap(char[] s, int l, int r){
        char c = s[l];
        s[l] = s[r];
        s[r] = c;
    }
}
```

```ruby
def reverse_string(s)
    s.reverse!
end
```

[520. Detect Capital](https://leetcode.com/problems/detect-capital/)
```java
class Solution {
    public boolean detectCapitalUse(String word) {
        if(word == null || word.length() < 1){
            return true;
        }
        int count = 0;
        for(int i = 0; i < word.length(); i++){
            char c = word.charAt(i);
            if(Character.isUpperCase(c)){
                count++;
            }
        }
        if(count == word.length() || count == 0){
            return true; //first and second condition
        } else if (count == 1 && Character.isUpperCase(word.charAt(0))){
            return true; // third condition;
        } else{
            return false;
        }
        
    }
}
```

```ruby
def detect_capital_use(word)
    word == word.upcase || word == word.downcase || word == word.capitalize
end
```

[557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/)

```java
class Solution {
    public String reverseWords(String s) {
        if(s == null || s.length() <= 1){
            return s;
        }
        String[] words = s.split(" ");
        for(int i = 0; i < words.length; i++){
            words[i] = reverse(words[i]);
        }
        return String.join(" ", words);
    }
    private String reverse(String word){
        StringBuilder sb = new StringBuilder();
        for( int i = word.length() - 1; i >= 0; i--){
            sb.append(word.charAt(i));
        }
        return sb.toString();
    }
}
```

```ruby
def reverse_words(s)
    s.split(" ").map{ |str| str.reverse}.join(" ")
end
```

[125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

```java
class Solution {
    public boolean isPalindrome(String s) {
        if(s.length() <= 1){
            return true;
        }
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < s.length(); i++){
            char c = s.charAt(i);
            if(Character.isLetterOrDigit(c)){
                sb.append(Character.toLowerCase(c));
            }
        }
        return valid(sb.toString());
    }
    private boolean valid(String s){
        int l = 0, r = s.length() - 1;
        while(l < r){
            if(s.charAt(l++) != s.charAt(r--)){
                return false;
            } 
        }
        return true;
    }
}
```

```ruby
def is_palindrome(s)
    return true if s.nil? || s.length <= 1
    
    letters = ("a".."z").to_a + ("0".."9").to_a
    str = ""
    for i in 0...s.length
        str += s[i].downcase if letters.include?(s[i].downcase)
    end
    str == str.reverse
end
```

[345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

```java
class Solution {
    public String reverseVowels(String s) {
        if(s == null || s.length() <= 1){
            return s;
        }
        char[] chars = s.toCharArray();
        String  vowels = "aeiouAEIOU";
        int l = 0, r = s.length() - 1;
        while(l < r){
            while(l < r && vowels.indexOf(s.charAt(l)) == -1){
                l++;
            }
            while(l < r && vowels.indexOf(s.charAt(r)) == -1){
                r--;
            }
            if(l >= r){
                break;
            }
            swap(chars, l++, r--);
        }
        return new String(chars);
        
    }
    private void swap(char[] chars, int l, int r){
        char c = chars[l];
        chars[l] = chars[r];
        chars[r] = c;
    }
}
```

```ruby
def reverse_vowels(s)
    return s if s.nil? || s.length <= 1
    vowels = "aeiouAEIOU"
    l, r = 0, s.length - 1
    while l < r
        while l < r && !vowels.include?(s[l])
            l += 1
        end
        while l < r && !vowels.include?(s[r])
            r -= 1
        end
        if l >= r
            break
        end
        s[l], s[r] = s[r], s[l]
        l += 1
        r -= 1
    end
    s
end

```

[14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) 
            return "";
        String pre = strs[0];
        for (int i = 1; i < strs.length; i++)
            while(strs[i].indexOf(pre) != 0)
                pre = pre.substring(0,pre.length() - 1);
        return pre;
    }
}
```

```ruby
def longest_common_prefix(strs)
    return "" if strs.nil? || strs.length <= 0
    pre = strs[0]
    for i in 0...strs.length
        while strs[i].index(pre) != 0
            pre = pre[0...pre.length - 1]
        end
    end
    pre
end
```

[476. Number Complement](https://leetcode.com/problems/number-complement/)

```java
class Solution {
    public int findComplement(int num) {
        int i = 0;
        int j = 0;
        
        while (i < num){
            i += Math.pow(2, j);
            j++;
        }
        return i - num;
    }
}
```