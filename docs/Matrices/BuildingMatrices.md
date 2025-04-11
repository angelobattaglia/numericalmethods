# Building Mats

## Basic Vectors
Column vector of 4s

```matlab
d = 4*ones(4, 1)
```

```shell
d =

   4
   4
   4
   4
```

We can transpose it, turning it into a row vector

```matlab
d = 4*ones(4, 1)'
```

```shell
d =

   4   4   4   4
```

## Putting vectors into matrices, diagonally

This is how you put a vector in the diagonal of a matrix
```matlab
diag(ones(1,4), 0)
```
so that..
```shell
ans =

Diagonal Matrix

   1   0   0   0
   0   1   0   0
   0   0   1   0
   0   0   0   1
```

Putting the vector in the superdiagonal directly above the elements comprising the diagonal  

```matlab
diag(ones(1,4),1)
```
```shell
ans =

   0   1   0   0   0
   0   0   1   0   0
   0   0   0   1   0
   0   0   0   0   1
   0   0   0   0   0
```

and Subdiagonal, i.e. directly below ..
```matlab
diag(ones(1,4),-1)
```
```shell
ans =

   0   0   0   0   0
   1   0   0   0   0
   0   1   0   0   0
   0   0   1   0   0
   0   0   0   1   0
```

Now, building a typical matrix:

```matlab
A = -2*eye(5) + diag(ones(1,4),1) + diag(ones(1,4),-1);
```
```shell
A =

  -2   1   0   0   0
   1  -2   1   0   0
   0   1  -2   1   0
   0   0   1  -2   1
   0   0   0   1  -2
```

`eye(n)` creates an Identity matrix of order `n`

## Algorithm for the Anti-Diagonal

To build an anti-diagonal matrix

```matlab
% The anti-diagonal matrix

n = 4;
C = eye(n);
tmp = zeros(n, 1);

for i = 1:n/2
    tmp = C(:, i);
    C(:, i) = C(:, n-i+1);
    C(:, n-i+1) = tmp;
end

% to show it ..
C
```
```shell
C =

   0   0   0   1
   0   0   1   0
   0   1   0   0
   1   0   0   0
```

## Composing Matrices

This combines the matrices into a bigger one
```matlab
A = [B, C; C, D]
```
of course, try to avoid dimensions mismatch


