# Principal Component Analysis (PCA)
## Rough Understanding
PCA is a **dimensionality-reduction method**. This [link](https://builtin.com/data-science/step-step-explanation-principal-component-analysis) may get you a detailed explaination about PCA.

* standardize the range. 归一化
* compute the **covariance matrix**. see the relationship among the input datas.
* get the **EVD** or **SVD** of **covariance matrix**.
    - Principal Components -> more varient, *purple line*
    <img src="./imgs/Principal Component Analysis second principal.gif"> 
    - EVD is how we get purple lines

## Explaination of why covariance matrix is the key
Deep learning, [2.12](https://exacity.github.io/deeplearningbook-chinese/Chapter2_linear_algebra/)
