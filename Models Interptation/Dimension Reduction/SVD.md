## Singular value

Remind that the eigenvectors and eigenvalues of a symmetric matrix $A$ indicates the direction and magnitude of its shrinkage effects on a vector $x$. What if the matrix $A$ is not symmetrix or even not square?

Now, assume $A$ $\in$ $R^{m, n}$ and $x$ $\in$ $R^n$ such that $||x||=1$ wlog, then what is the directions and lengths of the srtetching effect of $A$ on $x$ by $Ax$ ? The answers are $Av$ and $\sigma=||Av||$ where $v$ is the eigenvetors of $A^TA$, which are referred as singular vector and singular value.

![image](https://github.com/zhenyan-wu/ML-Note/assets/115028750/b334bb36-e3f2-4d9b-9364-6d1634e592fb)

### Why $v$ and $\sigma$ ?
By definition, the maximum stretched direction of $A$ is $u_1=Ax^\*$ such that $||Ax^\*||$ is the maximum of $||Ax||$ and the second direction is the maximum one in the unit sphere perpendicular to $x^\*$. Notice that for a symmetric matrix, the stretching direction remains the same in the original normal sphere ($x^\* \propto Ax^\*$) but it is not ensured for a general matrix.

#### Proof

Let $x \in R^n$, $||x|| = 1$ and { $v_1, ..., v_n$ } be the basis so that 

$$ x = x_1v_1 + ... + x_nv_n $$

then

$$
\begin{alignat*}{2}
||Ax||^2 &= {x}^TA^TAx \\
& =  {(x_1v_1 + ... + x_nv_n)}^T{(\lambda_1x_1v_1 + ... + \lambda_nx_nv_n)} \\
& = {(\lambda_1x_1^Tx_1 + ... + \lambda_nx_n^Tx_n)}
\end{alignat*}
$$

Since $x_1, ..., x_n \in \(0, 1 \)$, the maximum of $||Ax||$ is obtained at $x^\* = (1, 0, ..., 0) = v_1$ as required.

Thus, multiply by the eigenvectors of $A^TA$ are the stretching directions of rectangular matrix $A$.

#### REMARKS--The stretching directions are also perpendicular
Let $u_1=Av_1$, $u_2=Av_2$ and $v_1$, $v_2$ are the eigenvectors of $A^TA$, then $v_1^Tv_2=0$ and $u_1^Tu_2={v_1}^TA^TAv_2=0$

