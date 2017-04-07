## Recursion

Recursion is an important concept in Miranda, as it is in many functional languages. It involves defining a function using itself, in order to implement something which might be more difficult if recursion could not be done.

A famous example is the Fibonacci sequence, where the next number is the sum of the previous two numbers.

In Miranda, we can write it like so:

```
|| Function to compute the n'th Fibonacci number
fib :: num->num
fib 0 = 0
fib 1 = 1
fib n = fib (n-1) + fib (n-2)
```

Execution examples:

```
Miranda> fib 1
1
Miranda> fib 0
0
Miranda> fib 4
3
Miranda> fib 10
35
```

Miranda will find the function, and work from the top down, to find a definition which fits the arguments given. For the examples above:

 - `fib 1`: We check if it fits the first definition, `fib 0`. As it does not, we check the second definition, `fib 1`. It fits, so we return `1`.
 - `fib 0`: We check if it fits the first definition, `fib 0`. It fits, so we return `0`.
 - `fib 4`: We check if it fits the first definition, `fib 0`. As it does not, we check the second definition, `fib 1`. As it does not, we check the third definition, `fib n`. This fits, and so we return `fib (n-1) + fib (n-2)`. This calls `fib 3` and `fib 2`, and the process will happen again.
 - `fib 10`: This will work similarly to `fib 4`, except we will call the `fib` function on many more arguments than to `fib 4`.

 Recursion is useful because several methods can be simply expressed (like the Fibonacci sequence) using recursion, than via the iterative method. You'll find that Miranda has many uses for recursion.
