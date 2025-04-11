# Gradient Descent

## Steepest Descent
When implementing a gradient-based method (or performing any linear algebra computations related to a system like 𝐴𝑥 = 𝑏) you want to use matrix multiplication (using `*`) rather than elementwise multiplication (`.*`).


```matlab
B = magic(n);
A = B'*B;
b = sum(A,2);
```

The initial vector `x` and the initial residual vector `r`
```matlab
x = (1:5)';
r = b-A*x;
```

The gradient descent method
```matlab
for m = 1:30
    a = (r'*r)/(r'*A*r);
    x = x+a*r;
    r = b-A*x;
end
```

Say you want to compute the absolute error in `norm-2`, since we stated
that the solution is the ones vector
```matlab
err = norm(ones(n,1)-x)
```

## Conjugate gradient without preconditioning, implemented natively in MATLAB

```matlab
% Setting up the computation
clear all
close all
format short e
```

```matlab
% Setting up the matrices
n = 2000;
A = 5* eye(n) + diag(2*ones(n-5,1), 5) + diag(2*ones(n-5,1),-5);
b = ones(n,1);
```

MATLAB’s pcg function stands for `Preconditioned Conjugate Gradient`.
```matlab
[x,FLAG,RELRES,ITER] = pcg(A,b)
```

Let's go over the details of the output `[x, FLAG, RELRES, ITER]`:
- `x`: is the solution of `Ax=b`.
- `FLAG`: A convergence flag. A flag of 0 typically indicates that the algorithm has converged successfully.
- `RELRES`: The relative residual, which provides a measure of the accuracy of the computed solution.
- `ITER`: The number of iterations the algorithm took to converge.

## Note: Why Use a Ones Vector?
**Simplicity and Clarity**
- By choosing a vector of ones, the system is set up in a simple, easily understandable way. This makes it straightforward to analyze the behavior of the algorithm without the complications that might arise from a more complex or random right-hand side.

**Benchmarking the Algorithm**
- When testing or demonstrating the conjugate gradient method, using a uniform vector like this allows you to see how the algorithm converges on a known and controlled problem. It helps in evaluating the performance and accuracy of the method.

**Consistency**
- In many numerical experiments, especially in educational settings or initial testing, a ones vector is commonly used. This is because it provides a consistent and repeatable scenario for comparing the iterative solution with theoretical expectations.

**Numerical Stability**
- A right-hand side with all ones avoids introducing additional scale issues or numerical instabilities that might occur with more varied entries. This ensures that any observed behavior in the convergence of the algorithm is more likely due to the properties of 𝐴.
A and the method itself, rather than an artifact of the vector 𝑏.