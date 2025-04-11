# Interpolation using polyval and polyfit

## Polyval and Polyfit

To interpolate a function f(x) over an interval (-2, 4) in 7 nodes,
first, we need to define the 7 nodes belonging to the x-axis

```matlab
n_nodes = 7; % just specifying at the beginning the number of nodes
x_nodes = linspace(-2, 4, 7)
```

Secondly, we need to compute the f(x) in these seven nodes, calling the vector y
```matlab
y_nodes = f(x_nodes)
```

Ultimately, with `polyfit` we compute the *coefficients* of these polynomials,
as a vector. We only need the coefficients to discriminate a single polynomial form
```matlab
p_coeffs = polyfit(x_nodes, y_nodes, n_nodes - 1)
```

Now, I can evaluate the polynomial either over an interval or a point

- over an interval *z*
```matlab
z = linspace(-2, 4, 1000); % I want the interval to be dense of points
p = polyval(p_coeffs, z);
```

- over a point
```matlab
p = polyval(p_coeffs, 0.75);
```

## Error estimation

There are ways to compute the error, whether relative or absolute
