# CMPS 2200  Recitation 03

**Name**_________________________  


In this recitation, we will investigate recurrences for work and span of algorithms. Unlike other recitations, you may add your answers directly to this document. You do not need to use an `answers.md`.

## Tree method (9 pts)
Solve the following recurrences using the tree method. 

a) $W(n) = 3W(n/4) + n^2$

Level 0: $n^{2}$  

Level 1: 3 calls of $(\frac{n^{2}}{16}) = 3(\frac{n^{2}}{16}) = \frac{3n^{2}}{16}$

Level $i$: $3^{i}$ calls of $(\frac{n^{2}}{16^{i}}) = \frac{3^{i}n^{2}}{16^{i}}$

$\frac{3}{16} < 1$, so it is decreasing geometrically

The size of a sub-problem at level $h$ is $\frac{n}{4^{h}}$

The base case happens when $\frac{n}{4^{h}}$, so when $n = 4^{h}$ -> $h = log{_4}{n}$

$\sum_{i=0}^{\log_4 n - 1} n^2\left(\frac{3}{16}\right)^i$ = $θ(n^{2})$
The leaves contribute $n^{log{3}}$ which is smaller, so $W(n) = θ(n^{2})$

b) $W(n) = W(n/3)+ W(2n/3) + n \log n$

Level 1: 2 calls of sizes $\frac{n}{3}$ and $\frac{2n}{3}$ with work of $log{\frac{n}{3}} = (\frac{n}{3})log{\frac{n}{3}} + (\frac{2n}{3})log{\frac{2n}{3}}$

For each level where no nodes have reached their base case, the subproblems sum to size n

So, any sub-problem with size $m$ has a local work of $mlog{m}$, or at most $O(nlog{n})$

The shortest branch is the repeated $\frac{n}{3}$ branch, which has a height of $log{_3}{n}$

The longest branch is the repeated $\frac{2n}{3}$ branch, which has a height of $log{_\frac{3}{2}}{n}$, so branch height is $θ(log{n})$

This gives $W(n) = θ(log{n}) \dot O(nlog{n}) = θ(nlog^{2}{n})$

c) $W(n) = 2W(n/2)+ n/ \log n$

Level $i$: $2^{i}$ sub-problems with local work of $\frac{\frac{n}{2^{i}}}{log{\frac{n}{2^{i}}}}$ multiplying by the amount gives $\frac{n}{log{\frac{n}{2^{i}}}}$

If using asymptotic analysis, we assume a log base of 2, $log{\frac{n}{2^{i}}} = log{n} - i$ so the work for each level is $\frac{n}{log{n}-i}$

The height of the tree is $h = log{_2}{n}$

This gives $\(\sum_{i=0}^{\log_2 n - 2} \frac{n}{\log_2 n - i}\)$ as the summation of the work of all levels

After factoring out the $n$ in the numerator, there is a harmonic series giving the final summation of $nlog{log{n}}$

Base calls from the leaves only give $O(n)$, so $W(n) = O(nlog{log{n}})$



## Brick method (6 pts)
Solve the following recurrences using the brick method. First argue
whether they are root-dominated, leaf-dominated, or balanced. Then,
state the resulting asymptotic bound for $W(n)$.

d) $W(n) = 2 W(0.49 n) + 1.01 n$

Using the Brick Method, this recurrence is root dominated by $1.01n$, so $W(n) = θ(n)$


e) $W(n) = W(n/2) + W(n/4) + 0.999n$
.  
.  
.  
.  
.  
.  
.  
.  
.  


## Bonus (3 pts)

Solve the following recurrence.

f) $W(n) = \sqrt{n}W(\sqrt{n}) + \sqrt{n}$
.  
.  
.  
.  
.  
.  
.  
.  
.  

