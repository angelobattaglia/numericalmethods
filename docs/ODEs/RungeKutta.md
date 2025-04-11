# Runge Kutta (Heun's Method)


format short e

x0 = 2; % Interval starting point
xN = 3; % Interval ending point
y0 = 1; % initial condition
N = 8; % sub-intervals

Then, I define the step size
```matlab
% step
h = (xN - x0) / N;
```

```matlab
% Inizializzo x e y, e prealloco
x = (x0:h:xN)'; % Note: it's a row vector
y = zeros(N+1, 1);
y(1) = y0;
```

% Function handle per f(x, y)
f = @(x, y) (x .* y) ./ ((x - 1).^2); 
% This "x.*y" vector product is the reason why we put x as
% a row vector

% Heun's method
for n = 1:N
    K1 = f(x(n), y(n));
    K2 = f(x(n) + h, y(n) + h * K1);
    y(n+1) = y(n) + (h / 2) * (K1 + K2);
end

% Exact solution
y_exact = @(x) (x-1).*exp((x - 2) ./ (x - 1));

% Vettore deglie errori e il massimo di questo vettore
error = abs(y(end) - y_exact(3));