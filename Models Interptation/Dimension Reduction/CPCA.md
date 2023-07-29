## Covariance-free PCA
PCA is a variance-focused approach but the naive covariance method is rarely used because it is not efficient due to high computational and memory costs of explicitly determining the covariance matrix. The covariance-free approach avoids the $np^2$ operations of explicitly calculating and storing the covariance matrix $X^TX$, instead utilizing one of matrix-free methods, for example, based on the function evaluating the product $X^T(Xv)$ at the cost of $2np$ operations. [Wiki-Pedia]

One of the famous covariance-free PCA algorithm is introduced by Juyang Weng [http://www.cse.msu.edu/~weng/research/CCIPCApami.pdf], referred as CCIPCA. The algorithm sequentially absorb data points and iteratively estimates the covariance matrix and estimate its eigenvectors. This algorithm maintains the statistical efficiency by constructing an efficient estimator so that the estimate has the smallest error variance provided by Caramer-Rao lower bound and therefore converges more quickly.

The pseudo-codes of CCIPCA is listed below.

