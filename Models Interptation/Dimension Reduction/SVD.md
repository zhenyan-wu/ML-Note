## Singular value

### Stretching
Remind that the eigenvectors and eigenvalues of a symmetric matrix $A$ indicates the direction and magnitude of its shrinkage effects on a vector $x$. What if the matrix $A$ is not symmetrix or even not square?

Now, assume $A \in R^{m, n}$, $m \ge n$ and $x$ $\in$ $R^n$ such that $||x||=1$ wlog, then what is the directions and lengths of the srtetching effect of $A$ on $x$ by $Ax$ ? The answers are $Av$ and $\sigma=||Av||$ where $v$ is the eigenvetors of $A^TA$, which are referred as singular vector and singular value.

<div align=center><img src="https://github.com/zhenyan-wu/ML-Note/assets/115028750/b334bb36-e3f2-4d9b-9364-6d1634e592fb"/></div>

### Why $v$ and $\sigma$ ?
By definition, the maximum stretched direction of $A$ is $u_1=Ax^{*}$ such that $||Ax^{*}||$ is the maximum of $||Ax||$ and the second direction is the maximum one in the unit sphere perpendicular to $Ax^{*}$. Before multiplying by $A$, the vectors on the original sphere are also orthogonal.

For a symmetric matrix, the stretching direction remains the same in the original normal sphere ($x^{*} \propto Ax^{*}$) but it is not ensured for a general matrix.

#### Proof

Let $x \in R^n$, $||x|| = 1$ and { $v_1, ..., v_n$ } be an orthonormal basis

$$ x = x_1v_1 + ... + x_nv_n $$

then

$$
\begin{alignat*}{2}
||Ax||^2 &= {x}^TA^TAx \\
& =  {(x_1v_1 + ... + x_nv_n)}^T{(\lambda_1 x_1v_1 + ... + \lambda_n x_nv_n)} \\
& = {(\lambda_1x_1^2 + ... + \lambda_n x_n^2)}
\end{alignat*}
$$

Since $x_1, ..., x_n \in (0, 1)$, the maximum of $||Ax||$ is obtained at $(1, 0, ..., 0) = v_1$.

Similarly, the second stretched direction is difined as the vectors with the maximum length, which is perpendicular to $Av_1$. Assume the direction is $Ay$, $y \in R^n$, $||y|| = 1$ such that $y^TA^TAv_1=0$, which is $y^Tv_1=0$. 

$$ y = y_1v_1 + ... + y_nv_n $$

If $y^Tv_1=0$, the first coordinate $y_1$ is zero. That is 

$$ y = y_2v_2 + ... + y_nv_n $$

then

$$
\begin{alignat*}{2}
||Ay||^2 &= y^TA^TAy \\
& =  {(y_2v_2 + ... + y_nv_n)}^T{(\lambda_2y_2v_2 + ... + \lambda_n y_nv_n)} \\
& = {(\lambda_2y_2^2 + ... + \lambda_n y_n^2)}
\end{alignat*}
$$

Again, the maximum of $||Ay||$ is obtained at $(0, 1, 0, ..., 0) = v_2$.

Further induction can be shown similarly. Thus, multiply by the eigenvectors of $A^TA$, $\{Av_1, Av_2, ..., Av_n \}$ are the stretching directions of rectangular matrix $A$.

As $\{v_1, v_2, ..., v_n \}$ are orthonormal vectors, the stretching length is the norm of $\{Av_1, Av_2, ..., Av_n \}$



### Another side?
We have investigated the case by right multiplication. What about from the other side?

For an $m$ by $n$ matrxi $A$, $\{ v_1, v_2, ... , v_n\}$ are the eigenvectorfor $A^TA$,

$$ A^TAV = V\Lambda_n $$

Similarly, $\{ u_1, u_2, ... , u_m\}$ are the eigenvectorfor $AA^T$,

$$ AA^TU = U\Lambda_m $$

$V$ and $U$ are both orthonormal matrixs that $O^TO=I$.

Now, without loss of generality, assume that $m \ge n$ and the rank of $A$, $r_A=n$, which means $A$ has $n$ independent column vector and therefore $n$ orthorgonal eigenvectors and $n$ non-zero eigenvalues.

As $A^TA$ and $AA^T$ have the same rank as $A$, they also both have $n$ eigenvectors and eigenvalues. One can show the eigenvalues actually the same. 

From $A^TAV = V\Lambda_n$, we can have $AA^T(AV) = (AV)\Lambda_n$. $AV \in R^{m,n}$ and $\Lambda_n \in R^{n,n}$ which can be extended to $\Lambda_m \in R^{m,m}$ by adding zero entries. It is because that the last $m-n$ diagonal entries of $\Lambda_m$ is zero. And $U$ can be extended to a orthonormal matrix by orthogornalization.

$$ \left[ \frac{AV}{||AV||}, U^{'}\right] = U $$

And, then

$$ 
\begin{alignat*}{2}
AA^T(AV) &= (AV)\Lambda_n \\
AA^T\left[ \frac{AV}{||AV||}, U^{'}\right] &= \left[ \frac{AV}{||AV||}, U^{'}\right]\left[ \Lambda_n, 0_{n,m}; 0_{m,n}, 0_{m-n,m-n}\right] \\
AA^TU &= U\left[ \Lambda_n, 0_{n,m}; 0_{m,n}, 0_{m-n,m-n}\right] \\
AA^TU &= U \Lambda_m
\end{alignat*} 
$$

That is

$$ \Lambda_m = \left[ \Lambda_n, 0_{n,m-n}; 0_{m-n,n}, 0_{m-n,m-n}\right] $$


### Back to the geometry

As shown above, the assume the orginal space is $R^n$ and the projection space is $R^m$, $n \le m$. $\{ v_1, ..., v_n\}$ is an orthonormal basis in the original space. After projected by matrix $A \in R^{m,n}$, $\{ Av_1, ..., Av_n\}$ is the set of stretching directions in the projection space and it can be extended to a basis in the targeted space.


## Decomposition

$$
\begin{alignat*}{2}
\left[ {\frac{AV}{||AV||}}, U^{'} \right] \left[ ||AV||, 0_{m-n,n} \right]^T & = AV \\
U \left[ ||AV||, 0_{m-n,n} \right]^T &= AV \\
A &= U \left[ \sqrt{\Lambda_n}, 0_{m-n,n} \right]^T V^T \\
A &= U \Sigma V^T 
\end{alignat*}
$$

It can be also written explictly in terms of projection matrix $u_iv_i^T$

$$  \begin{alignat*}{2}
A &= \begin{bmatrix} u_1 & ... & u_m \end{bmatrix} \begin{bmatrix}
    \sigma_1 v_1^T \\
    ... \\
    \sigma_n v_n^T \\
    0 \\
    ... \\
    0
    \end{bmatrix} \\
  &= \sigma_1u_1v_1^T + ... + \sigma_nu_nv_n^T
    \end{alignat*}$$

$u_1v_1^Tx$ gives the projection of x onto the basic vector $u_1$ in the projection space. The length of such projection is not determined by $u_1$ but $v_1$ the basic vector in the original space. That is, the co-ordinate of $u_i$ in the target space is the scalar projection of $x$ on $v_i$.

For the rectangular matrix $A$, the projection of $x$ can be decomposed by only the first n basis vectors, and the length is scaled by the product of $\sigma_i$, the sigular value and $v_i^Tx$, the projection on the basis of original space.

<div align=center><img src="https://github.com/zhenyan-wu/ML-Note/assets/115028750/3c79a9ff-9b0f-45b7-b704-42679e6d4903"/></div>


