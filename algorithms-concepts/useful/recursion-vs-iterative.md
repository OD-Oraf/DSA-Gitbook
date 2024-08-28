# Recursion vs iterative

## Why is iterative generally faster than recursion

* Overhead of Function Calls
  * Recursion requires additional memory for each function call
    * Includes space for parameters, local variables and return address
  * In contrast the iterative approach uses single set of variables that are updated within loop
  * Additional calls on the stack frame may possibly result in a stack overflow
