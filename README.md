# Factorial Trailing Zeroes
## https://leetcode.com/problems/factorial-trailing-zeroes

Given an integer n, return the number of trailing zeroes in n!.
```
Example 1:

Input: 3
Output: 0
Explanation: 3! = 6, no trailing zero.

Example 2:

Input: 5
Output: 1
Explanation: 5! = 120, one trailing zero.
```
**Note: Your solution should be in logarithmic time complexity.**

## Approach :
Lets see some examples
5! = 1 * 2 * 3 * 4 * 5 = 1 trailing zero
7! = 1 * 2 * 3 * 4 * 5 * 6 * 7 = 1 trailing zero
10! = 1 * 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9 * 10 = 2 trailing zeroes
15! = 1 * ... * 5 * .... * 10 * ... * 15 = 3 trailing zeroes
20! = 1 * ... * 5 * .... * 10 * ... * 15 * ... * 20 = 4 trailing zeroes
25! = 1 * ... * 5 * .... * 10 * ... * 15 * ... * 20 * .... * 25 = 6 trailing zeroes (25 = 5 * 5)

So basically we have to count how many times 5 will come, while calculating factorial of a number.
Number of trailing zeroes will be equal to number of 5's.


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
            n = n /5; 
            trailingZeroes += n;
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
