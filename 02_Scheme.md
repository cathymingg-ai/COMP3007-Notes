# Scheme
*Lecture 2*

### Origins of Computability and Programming Languages
- 1930s: Lambda Calculus by Alonzo Church and Turing Machines (1930s)
    - **Church-Turing Thesis:** combination of Lambda calc and Turing Machines
- 1950s: **Lisp** was created by John McCarthy (based on lambda calc)
- functional programming emerged from **symbolic substitution**

## 1. Historical Context of Lisp and Scheme
### Lisp (1950s)
- symbolic computation ~ *LISt Processing*
- first-class functions, recursion, garbage collection
### Scheme (1975)
- Minimalist dialect from the Lisp family (1950's by John McCarthy)
- By Steele and Sussman (1975) 
    #### Why Scheme?
    - Minimal syntax: clear and simple
    - for functional programming and abstraction
    - supports first-class functions and recursions. *See example:*
        ```scheme
        (define (cube x) (* x x x))
        (cube 3)                    ; Output: 27

    ### 1.1 Primitive Values
    - integers (3), rationals (1/5), reals (3.14159), complex (0+3i)
    - Boolean: #t for true, #f for false

    ### 1.2 Combinations
    - **Prefix Notation** - combining expressions => applying a procedure to arguments
    - a systematic process, reducing expressions
    - follow BEDMAS
        ### Prefix Notation
        ```scheme
        ; Example 1
        2 + 3 * 4     ; before
        (+ 2 (* 3 4)) ; prefix 
                      ; prefix effect = easy to read
        ; Example 2 - no limit to nesting depth
        (+ (* 2 3)- 10 4)   ; Output: 12   
        ```

        ### Evaluating Combinations: Step-by-step  
        - Recursive: **Scheme evaluates sub-expressions first**
        ```scheme
        (* (+ 2 3) (- 7 4)) ; Step-by-step
        (+ 2 3) ; => 5
        (- 7 4) ; => 3
        (* 5 3) ; Output: 15
        ```
        ```scheme
        (*(+ 2(* 4 6))(+ 3 5 7))
        (+ 3 5 7) ; => 15
        (* 4 6)   ; => 24
        (+ 2 (24)); => 26
        (* 26 15) ; Output: 390
        ```
        ```scheme
        (* (+ 3 4) (/ 8 2))
        (/ 8 2) ; => 4
        (+ 3 4) ; => 7
        (* 7 4) ; Output: 28
        ```

## 2. Review Scheme IDE
- IDE for Scheme in this class is **DrRacket**
    - Setup: **R5RS** 
- **REPL** is an interpreter for Scheme Expressions 
    - you type an expression, press Enter
    - Scheme reads, evaluates and prints the result; then loops for more

## 3. Symbolic Abstraction
*Scheme Syntax*
- **SYMBOLIC ABSTRACTION** Associating meaning to values using names (/symbols)
- Naming rules:
    - can include capital and small letters
    - valid special characters: ?!+-*/<>=:$%&_^
    - cannot start of + or - or a digit
    - not case-sensitive
    ```scheme
    (define size 2)  ; example
    ```
- **Advantage of Symbolic Abstraction**
    1. Simplifies Effort
    2. Abstraction of Implementation Details
    3. Supports 'Incremental' Development

- **Type Checking: Static or Dynamic**
    - Type Checking - determines if an operation is valid for certain operands
    - **Static** - checked at comppile-time
    - **Dynamic** - checked at runtime
        - Scheme is dynamically typed => everything is determined at runtime.
- display Procedure i.e., (display expression) => prints argument to standard output
- (newline) => output line break
- (read) => prompt for user input


## 4. Procedure Abstraction
*Defining & Using Compound Procedures*
- *Procedural Abstraction*
    - "black box" abstraction
    - grouping of expressions forming compound operation
    ```scheme
    (define (<name> <parameters>) <body>)
    (define (square x) (* x x))

    ; <name>: Bound to the procedure object
    ; <parameters>: Symbols to receive objects
    ; <body>: Expressions evaluated in sequence
    ```
    - Example of Procedure calls: creating a square procedure (you can also create an idenity this way, the procedure is similar)
    ```scheme
    (define (square x)
    (* x x))
    (square 2) ;Output 4
    ```
    - Procedure calls includes (not limited to): square root, sum-of-squares, cube, sum-of-cubes, double-sum, and more... 
    - Algorithm & syntax goes hand-in-hand
