# Factorial Trailing Zeroes
## https://leetcode.com/problems/factorial-trailing-zeroes

Given an integer n, return the number of trailing zeroes in n!.

Example 1:

Input: 3
Output: 0
Explanation: 3! = 6, no trailing zero.

Example 2:

Input: 5
Output: 1
Explanation: 5! = 120, one trailing zero.

**Note: Your solution should be in logarithmic time complexity.**


# Implementation 1 : Naive (Time Limit Exceeded 😀)
```java
import java.math.BigInteger;

class Solution {
    public int trailingZeroes(int n) {
       // Calculate n!
    BigInteger nFactorial = BigInteger.ONE;
    for (int i = 2; i <= n; i++) {
        nFactorial = nFactorial.multiply(BigInteger.valueOf(i));
    }
    
    // Count how many 0's are on the end.
    int trailingZeroes = 0;
    while (nFactorial.mod(BigInteger.TEN).equals(BigInteger.ZERO)) {
        nFactorial = nFactorial.divide(BigInteger.TEN);
        trailingZeroes++;
    }
    
    return trailingZeroes;
   }
}
```
# Implementation 2 : 
```java
class Solution {
    public int trailingZeroes(int n) {
        int trailingZeroes = 0;  
        while(n >= 5) {
            trailingZeroes += (n / 5);
            n = n /5; 
        }
        return trailingZeroes;
    }
}
```

# References :
1. https://www.geeksforgeeks.org/biginteger-class-in-java
2. https://docs.oracle.com/javase/7/docs/api/java/math/BigInteger.html
3. https://leetcode.com/articles/factorial-trailing-zeroes
4. https://www.youtube.com/watch?v=3Hdmv_Ym8PI
