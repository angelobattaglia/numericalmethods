# General Method for Solving Integrals in MATLAB

The easiest way to compute an integral

```matlab
format short e

% Define your function
f = @(x) x.^2 + sin(x);

% Compute the integral from a to b
a = 0;      % Lower limit
b = pi;     % Upper limit

I = integral(f, a, b);
I
```
