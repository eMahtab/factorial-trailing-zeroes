# Factorial Trailing Zeroes
## https://leetcode.com/problems/factorial-trailing-zeroes

# Implementation : Naive (Time Limit Exceeded 😀)
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

# References :
1. https://www.geeksforgeeks.org/biginteger-class-in-java
2. https://docs.oracle.com/javase/7/docs/api/java/math/BigInteger.html
3. https://leetcode.com/articles/factorial-trailing-zeroes
