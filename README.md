# 🚀 Power Function Implementation (`pow(x, n)`)  

## 📌 Problem Statement  
The goal is to implement a function `myPow(x, n)`, which computes `x` raised to the power `n` (i.e., \( x^n \)) efficiently. The function should handle both **positive and negative exponents**.

### 🔹 Example Inputs & Outputs  

| **Input**                      | **Output**    | **Explanation**                                      |
|--------------------------------|-------------|--------------------------------------------------|
| `x = 2.00000, n = 10`         | `1024.00000`  | \(2^{10} = 1024\) |
| `x = 2.10000, n = 3`          | `9.26100`     | \(2.1^3 = 2.1 \times 2.1 \times 2.1 = 9.261\) |
| `x = 2.00000, n = -2`         | `0.25000`     | \(2^{-2} = 1/2^2 = 1/4 = 0.25\) |

---

## 📝 Approach  

The function is implemented using **Exponentiation by Squaring**, which reduces the time complexity from **O(n) → O(log n)**.  

### **Key Observations**
- If `n` is **negative**, we convert the problem into its reciprocal:  
  \[
  x^{-n} = \frac{1}{x^n}
  \]
- If `n` is **odd**, multiply `x` once and reduce the exponent by `1`.
- If `n` is **even**, square `x` and divide `n` by `2` to reduce steps.

---

## 🏗️ Java Implementation  

### 💻 Code:
```java
class Solution {
    public double myPow(double x, int n) {
        // Handling negative exponent
        if (n < 0) {
            x = 1 / x;
            n = -n;
        }

        double result = 1; // Initialize result to 1

        while (n != 0) {
            if (n % 2 != 0) {  // If n is odd, multiply the result by x
                result *= x;
            }
            x *= x;  // Square x
            n /= 2;  // Reduce n by half
        }

        return result;
    }
}
```

---

## ⏳ Complexity Analysis  

| **Operation**        | **Time Complexity** | **Space Complexity** |
|----------------------|--------------------|--------------------|
| **Exponentiation**   | **O(log n)**       | **O(1)** (iterative approach) |

---

## 🔧 Edge Cases Considered
✅ `x = 0, n = 0`: Should return `1` (by definition, anything raised to power 0 is `1`).  
✅ `x = 0, n > 0`: Should return `0` (`0` raised to any positive power is `0`).  
✅ `x = 1, n = any`: Should return `1` (since `1` raised to any power remains `1`).  
✅ `x = -1, n = odd/even`: Should return `-1` or `1` respectively.  
✅ `n` is a large **negative** number (`Integer.MIN_VALUE`): We ensure safe handling.  



### Let me know if you'd like any changes! 🚀
