# Support vector machine
## rough understanding
SVM的线性函数可以重写为 $w^\mathrm T x+b=b + \sum_{i=1}^{m}{\alpha}_ix^\mathrm T x^{(i)}$, 其中$x^\mathrm T x^{(i)}$可以被替换成$k(x,x^{(i)})=\phi(x)\cdot\phi(x^{(i)})$,$k$为核函数，kernel function  

SVM is a classification-based algorithm  

* 扩大线性分类函数 $y = w^\mathrm T x + b$ 的边缘
    - maximize $\frac{2}{\|w\|}$ is also $\frac{1}{2}\|w\|^2$
    - a quadratic programming problem 
* kernel function
    
