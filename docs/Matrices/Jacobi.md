# Jacobi

```
% Jacobi
clear all
close all
clc
n = 20;
A = 5* eye(n) + diag(-1*ones(n-1,1), -1) + diag(-7*ones(n-2,1),2);
b = A * ones(n,1);
x = zeros(n,1); % Pre-allocation, and also we built it this way
D = diag(diag(A));
C = A - D;
tol = 1.0e-3;
for k = 1:1000
    x = D\(b-C*x);
    if norm(b - A*x ,2)/norm(b, 2) < tol
        break
    end
end
k
```


```
% % Jacobi
% clear all
% close all
% clc
% n = 10;
% A = 10* eye(n) + diag(3*ones(7,1), 3) + diag(-5*ones(5,1),-5);
% b = A * ones(n,1);
% x = (1:10)';
% D = diag(diag(A));
% C = A - D;
% tol = 1.0e-10;
% for k = 1:1000
    % x = D\(b-C*x);    
    % if norm(b - A*x ,2) < tol*norm(b, 2)
        % break
    % end
% end
% k


% Jacobi 9/15

n = 100;
A = 3*eye(n) + diag(ones(n-1, 1), -1) + diag(ones(n-1, 1), + 1);

sol = ones(n, 1);
b = A*sol;

D = diag(diag(A));
C = A - D;

x0 = linspace(0, 1, 20);

for i = 1:20
    x0 = D\(b-C*x);
    x = x0;
end

err = norm(abs(x - x0), inf);

fprintf('The result is: %.5e\n', err);
```
