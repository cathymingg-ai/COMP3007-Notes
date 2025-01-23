# Recursion
*Lecture 6, Readings: [https://mitp-content-server.mit.edu/books/content/sectbyfn/books_pres_0/6515/sicp.zip/full-text/book/book-Z-H-11.html#%_sec_1.2.1]*

**Procedure** is a pattern for the local evolution of computational process. Specifies how each stage of the process is built upon the previous stage.

## 1. Recursion
- function that calls itself to break down a problem. 
    - **base case:** next call moves towards an end point 
- this is used when a problem can be **divided into smaller problems**

    #### Steps to Solve Recursion Problems
    1. Understand the problem: put it in your own words
    2. Identify the base case: what causes us to stop the process?
    3. Identify recursive step: break problems into smaller problems
    4. Combine sub-problems' results
    5. Make sure you **stop**
    6. Test it!
    
    ### 1.1 First Problem: Factorial
    #### Problem Statement: 

        Compute the factorial of n -> n!
        n! = n * (n-1) * (n-2) * (n-3) *...* 2 * 1 
        0! = 1

    Here, we want to multiple ALL the numbers from n down to 1 not including 0 in the product.

    #### Base Case, Recursive Case
        Definition:
        n! = n * (n-1) * (n-2) * (n-3) *...* 2 * 1 
        0! = 1
    **Stop:** when n reaches 1
    
    **Recursive:** multiple our current value of n to the next value (n - 1)
    then call it again until we reach the base case.
        
        Factorial(n) = n * (n-1)

    **Progress:** towards the base case (n-1) until it reaches 1

### 2. Linear Recursive Process
- expansion followed by contraction
- state of the process is saved on the **stack**
- the interpreter keep track of the operations to be performed later on
- memory grows linearly with number of steps (n)
```scheme
#| A linear recursive process for computing 5! |#
;(factorial 5)
;(* 5 (factorial 4))
;(* 5 (* 4 (factorial 3)))
;(* 5 (* 4 (* 3 (factorial 2))))
;(* 5 (* 4 (* 3 (* 2 (factorial 1)))))
;(* 5 (* 4 (* 3 (* 2 1))))
;(* 5 (* 4 (* 3 2)))
;(* 5 (* 4 6))
;(* 5 24)
;120

#| This observation translates into a procedure: |#
(define (factorial n)
  (if (= n 1)
      1
      (* n (factorial (- n 1)))))
```

We can describe the computation by saying that the counter and the product simultaneously change from one step to the next according to the rule:

- **product <- counter · product**

- **counter <- counter + 1**

- and stipulating that n! is the value of the product when the counter exceeds n.

### 3. Linear Iterative Process
- resembles a logical control group
    - initial value, incrementation or counter, and max-count
    - there is a stop condition

    ```python
    # Python example:
    def factorial(n):
        acc = 1                     #initial value
        for x in range(1, (n+1)):   #incrementation process
            acc = acc * x
        return acc
    ```

    ### 3.1 Linear Iterative Process: Factorial
    #### Accumulator and Counter
    - keep a current running total of the factorial
    - increment the counter
    - stop once we reach the base case > n
    ```scheme
    (define (factorial-iter n)
        (define (fact-iter counter acc)
            (if (> counter n)
                acc
                (fact-iter (+ counter 1) (* acc counter))))
    (fact-iter 1 1))
    ```
    #### Substitution Model
    ```scheme
    ;(factorial-iter 5)
    ;(fact-iter 1 1)        ; counter acc
    ;(fact-iter 2 1)
    ;(fact-iter 3 2)
    ;(fact-iter 4 6)
    ;(fact-iter 5 24)
    ;(fact-iter 6 120)
    ;120
    ```
    - **Activation Record:** factorial-iter
    ### 3.2 Iterative Recursive Process
    - program is tail-recursive
        - no deferred operations
        - last operation is the recursive call
    - Scheme uses tail-call optimization
        - iterative process run in constant pace
        - number of steps grows linearly with n
            - memory remains constant

    **Tail-recursive implementation** is defined by a recursive function in which the recursive call is the last statement that is executed by the function.
    - iteration can be expressed using the ordinary procedure call mechanism (so that special iteration constructs are useful only as syntactic sugar)
    - **syntactic sugar** means it makes it easier to write code
        - *let* is the syntactic sugar for lambda (in let, you should evaluate & then bind)

### Keep in mind:
**Infinite Loop in a Linear Recursive Process** function will stop after it reaches the limit of the stack i.e., **Stack Overflow**

**Infinite Loop in a Linear Iterative Process** function will theoretically run forever.