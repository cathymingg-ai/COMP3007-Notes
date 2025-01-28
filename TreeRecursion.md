# Tree Recursion
*Lecture 7, Week 4*
Readings, Tree Recursion 1.2.2: [https://mitp-content-server.mit.edu/books/content/sectbyfn/books_pres_0/6515/sicp.zip/full-text/book/book-Z-H-11.html#%_sec_1.2.2]


#### Learning Outcomes:
1. Tree Recursion
    - Recursive Process
    - Iterative Process
2. First Class & Higher Order Procedures
    - Procedures as Arguments
______

# 1. Tree Recursion
- procedures calls itself more than once 
- each branch calls an addition recursive calls creating a tree-structure
**Characteristics of Tree Recursion:**
    - multiple recursive calls
    - calls can lead to exponential growth
    - redundant computations 

    ```Scheme
    ; Lecture Code
    (define (fib n)
    (cond ((= n 0) 0)
            ((= n 1) 1)
            (else (+ (fib (- n 1))(fib(- n 2))))))

    (fib 0)
    (fib 5)
    ;Output is 0 and 5

    ;Substitution Model: fib(5)
    ;(fib 5)
    ;(+ (fib 4 )(fib 3))
    ;(+ (+ (fib 3) (fib 2)) (+ (fib 2) (fib 1)))
    ;(+ (+ (+ (fib 2) (fib 1)) (+ (fib 1) (fib 0))) (+ (+ (fib 1) (fib 0)) 1))
    ;(+ (+ (+ (+ (fib 1) (fib 0)) 1) (+ 1 0)) (+ (+ 1 0) 1))
    ;(+ (+ (+ (+ 1 0) 1) 1)(+ 1 1))
    ;(+ (+ (+ 1 1) 1) 2)
    ;(+ (+ 2 1) 2)
    ;(+ 3 2)
    ```
*Note:* some notes in the slide are in the Recursion Slide already. 

### Recursive Process
### Iterative Process: Fibonacci
```Scheme
    (define (fib n)     ;function definition
        (define (fib-iter c n1 n2)      ;inner function definition that is responsible for iterative calculation (takes 3 parameters: c, n1, n2)
            (if (> c n)     ;base case: checks if c > n; if it is, return n1
                n1
            (fib-iter (+ c 1) (+ n1 n2) n1)))       ;recursive call
    (fib-iter 2 1 0))       ;initial call

    ;Substitution Model
    ;(fib 5)
    ;(fib-iter 2 1 0)
    ;(fib-iter 3 1 1)
    ;(fib-iter 4 2 1)
    ;(fib-iter 5 3 2)
    ;(fib-iter 6 5 3)

    ;Add Problem 1 (and review solution) from tge slides
```

# 2. First Class & Higher Order Procedures
**Example 1: Passing Procedure**
```Scheme
    (define (func1 x)
        (+ x 2))

    (define (func2 y)
        (y 3))
    ;(func2 4)
    ;(4 3)

    (func2 func1);
    ;(func1 3)
    ;(+ 3 2)    
    ; ~returns 5
```
**Example 2: Return a Procedure**
```Scheme
    (define (func3 x)
        (if (> x 0) + -))      
    (func3 100)     ;result #<procedure:+>
    (func3 -50)     ;result #<procedure:->
```
For line **(if (> x 0) + -)**
- if x > 0: expression evaluates to +
- if x < 0: expression evaluates to -

For returning procedure: **(func3 100)**
-  Result is: **<#procedure: +>**

*Lecture ended in slide 25*