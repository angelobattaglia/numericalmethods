# Gauss Seidel

With Gauss-Seidel the matrix A gets transformed with `tril(A)`.
We require a lower triagonal matrix.

```matlab
% Cleaning and choosing the number format
format short e
clear all
close all
clc
```

```matlab
% Building the matrix and the `Ax=b` system
n = 18;
A = 6*eye(n) + diag(-1*ones(n-1,1), 1) + diag(-1*ones(n-1,1), -1);
b = A*ones(n, 1);
x = zeros(n,1);
```

Preparing the `C` and `D` matrices used in the iterative method
```matlab
D = tril(A);
C = A - D;
```

```matlab
for k = 1:5
    x = D\(b-C*x);
end
err = norm(ones(n,1)-x)/norm(ones(n,1))
```

## Gauss-Seidel with residual vector check


```matlab
% Gauss-Seidel with residual vector check (6-23)

n = 20;
A = 5*eye(n) + diag(-1*ones(n-1, 1), -1) + diag(-7*ones(n-2, 1), 2);
b = A*ones(n, 1);
x = zeros(n, 1);
% Preparing the iteration matrix
D = tril(A);
C = A - D;
% Starting Flag set to false
flag = false;
% the starting point of the residual vector
r = b-A*x;
iterata = 0;

while ~flag
    % Gauss-Seidel Method
    x = D\(b-C*x); 
    r = b-A*x;
    if norm(r, 2) < 10^-3
        flag = true;
    end
    iterata = iterata + 1;
end
```
