# Chapter 1 - Basic Concepts  
## 1.1 Algorithms - Exercises  

### 1. the replacement notation

> The text showed how to interchange the values of variables m and n, using the replacement notation, by setting t &larr; m, m &larr; n, n &larr; t. Show how the values of *four* variables (a, b, c, d) can be rearranged to (b, c, d, a) by a sequence of replacements. In other words, the new value of a is to be the original value of b, etc. Try to use the minimum number of replacements. 

> try to rearrange **(a, b, c, d)** to **(b, c, d, a)** using minimum operations (replacements)

we need,  
a = b  
b = c  
c = d  
d = a  

It is cyclic in nature. we will need one temporary variable. 

**Solution**

1. temp &larr; a
2. a &larr; b
3. b &larr; c
4. c &larr; d
5. d &larr; temp


### 2. Prove m > n in E1

> Prove that m is always greater than n at the beginning of step [E1](../1.1%20-%20Algorithms/v01_ch01_n001.md), execpt possibly the first time this step occurs.

Algorithm E:  

E1: r = m % n  
E2: if r == 0: ans = n; terminate algorithm; else E3  
E3: m &larr; n, n &larr; r  

**Solution**  

for division (m / n) and remainder (r), it is true that (n > r).  
from step 2 onwards m = n and n = r, which implies m > n.  

Now for the cases where n > m in first step: 
fact: if n > m then r = (m % n) = m &rarr; r = m
> example: 10 % 100 = 10  
> 
so in the next step: m = n and n = r &rarr; m' = n, n' = r = m.
so m and n are swapped and from now onwards m' > n'

### 3. Change Algorithm E

> Change [Algorithm E](../1.1%20-%20Algorithms/v01_ch01_n001.md) (for the sake of efficiency) so that all trivial replacement operations such as "m &larr; n" are avoided. Write this new algorithm in the style of Algorithm E, and call it Algorithm F.  

current algorithm E: 

1. r = m % n
2. m &larr; n, n &larr; r
3. r = m % n
4. m &larr; n, n &larr; r
5. ...

Try to improve efficiency 

1. r = m % n
2. m &larr; r
3. r = n % m
4. n &larr; r
5. r = m % n
6. m &larr; r
7. r = n % m
8. n &larr; r
9. ...

**Solution**

**Algorithm F**: Improved version of Algorithm E. reduced replacement operations by half.

> F1. [Find Remainder] Divide m by n and let r be the remainder.  
> F2. [Is r 0?] If r = 0, terminate algorithm, n is the answer. else go to F3.  
> F3. [Reduce] m &larr; r  
> F4. [Find Remainder] Divide n by m and let r be the remainder.  
> F5. [Is r 0 ?] If r = 0, terminate algorithm, m is the answer. else go to F6.
> F6. [Reduce] n &larr; r, go to F1. 

### 4. GCD of 2166 and 6099

**Solution**

57

### 5. Show that the "Procedure for Reading This Set of Books" fails 3 out of 5 counts

> Show that the "Procedure for Reading This Set of Books" that appears in the preface actually fails to be a genuine algorithm on three of our five counts! Also mention some differences in format between it and Algorithm E.

**Solution**

### 6. What is T<sub>5</sub>, the average number of times step E1 is performed when n = 5 ?  

After E1 executes 1st time, the remainder will be in the set {0, 1, 2, 3, 4}.  

remainder 0 -> E1 will only be executed once - 1  
remainder 1 -> next time m = 5, n = 1. E1 will be executed twice - 2  
remainder 2 -> next time m = 5, n = 2. E1 will be executed thrice - 3  
remainder 3 -> next time m = 5, n = 3. E1 wil be executed four times - 4  
remainder 4 -> next time m = 5, n = 4. E1 will be executed thrice - 3  

at the start, m can be any integer, but they will fall into 5 categories shown above. 

we can say that the average T<sub>5</sub> will be the average of those 5 cases  

**Solution** 

T<sub>5</sub> = (1+2+3+4+3)/5 = 13/5 = 2.6