## Linear Algebra for ML

Notation: The set of all $m\times n$ real matrices will be denoted by $\mathbb{R}^{m\times n}$. The $i$-th column of a matrix $A$ will be denoted by $A_{i\bullet}$. The j-th column will be denoted by $A_{\bullet j}$.

---

Very important results [memorize]. NOT JUST MEMORIZE, internalize the results through plenty of examples, these should be second-nature.

**R1**. Let $A\in\mathbb{R}^{m\times n}, v\in\mathbb{R}^n$. Then $Av\in\mathbb{R}^m$ and $(Av)_i = (A_{i\bullet}).v$, which is the dot product of the $i$-th row of $A$ and $v$.

*Proof*. $(Av)_i = \sum_{k=1}^n A_{ik}v_k = (A_{i\bullet}).v$

**R2**. Similarly let $v\in\mathbb{R}^m,A\in\mathbb{R}^{m\times n}$. Then $vA\in\mathbb{R}^n$ and $(vA)_j=v.(A_{\bullet j})$. The proof is similar to that of R1.

**R3**. Let $A\in\mathbb{R}^{m\times n}, B\in\mathbb{R}^{n\times p}$. Then $(AB)_{\bullet j}=AB_{\bullet j}$.

*Proof*. Both sides of the equation are column vectors. Consider the $r$-th element of the RHS column vector: by R1, $(AB_{\bullet j})_r = (A_{r\bullet}).(B_{\bullet j})$.

Next, the $r$-th element of the column vector $(AB)_{\bullet j}$ or the $r$-th element of the $j$-th column of matrix $AB$, which is just $(AB)_{rj} = \sum_{k=1}^nA_{rk}B_{kj} = (AB_{\bullet j})_r = (A_{r\bullet}).(B_{\bullet j})$. The vectors on both sides are the same element-wise $\implies$ both vectors are the same.

**Note the following equivalence between summation and dot product convention. The repeated index that's being summed over (in Einstein summation convention, this is simply $A_i^k B_k^j$) will indicate a dot product.**
$\sum_{k=1}^n A_{ik}B_{kj} = (A_{i\bullet}).(B_{\bullet j}) = (AB)_{ij}$
$\sum_{j=1}^n A_{ij}v_j = (A_{i\bullet}).v = (Av)_i$
$\sum_{i=1}^n v_i A_{ij} =v.(A_{\bullet j}) = (vA)_j$

**R4**. Let $A\in\mathbb{R}^{m\times n}, B\in\mathbb{R}^{n\times p}$. Then $(AB)_{i \bullet}=A_{i \bullet}B$.

*Proof*. As before, $r$-th element of LHS $=(AB)_{ir} = (A_{i\bullet}).(B_{\bullet r})$. As for the RHS, $(A_{i \bullet}B)_r=(A_{i\bullet}).(B_{\bullet r})$ by R2.

**R5**. Let $v, x_1, \ldots, x_n\in\mathbb{R}^n$ such that $v=\sum_{k=1}^n\alpha_kx_k$ is a linear combination of the $x_k$'s. Then $v_i=\sum_{k=1}^n\alpha_k(x_k)_i$.

**R6**. In a multiplicative expression  $C_{ij}=\sum_{k=1}^nA_{ik}B_{kj}$, the free indices $i$ or $j$ can be replaced by $\bullet$ to give
$C_{\bullet j}=\sum_{k=1}^nA_{\bullet k}B_{kj}$
$C_{i\bullet}=\sum_{k=1}^nA_{ik}B_{k\bullet}$

Phrased alternatively, the $j$-th column of $C$ is a linear combination of $A$'s columns, which coefficients taken from the $j$-th column of $B$. Similarly, the $i$-th row of $C$ is a linear combination of $B$'s rows, with coefficients taken from the $i$-th row of $A$.

*Proof*. For the first expression, let's fix $j$ and vary $i$ from $1$ to $m$. We then have
$C_{1j}=\sum_{k=1}^nA_{1k}B_{kj} = A_{11}B_{1j}+A_{12}B_{2j}+\ldots+A_{1n}B_{nj}$
$C_{2j}=\sum_{k=1}^nA_{2k}B_{kj} = A_{21}B_{1j}+A_{22}B_{2j}+\ldots+A_{2n}B_{nj}$

$\vdots$

$C_{mj}=\sum_{k=1}^nA_{mk}B_{kj} = A_{m1}B_{1j}+A_{m2}B_{2j}+\ldots+A_{mn}B_{nj}$

Collecting the equations into column vectors,

$\begin{bmatrix}C_{1j}\\C_{2j}\\\vdots\\C_{mj}\end{bmatrix} = B_{1j}\begin{bmatrix}A_{11}\\A_{21}\\\vdots\\A_{m1}\end{bmatrix} + B_{2j}\begin{bmatrix}A_{12}\\A_{22}\\\vdots\\A_{m2}\end{bmatrix} + \ldots + B_{nj}\begin{bmatrix}A_{11}\\A_{2n}\\\vdots\\A_{mn}\end{bmatrix}$

or $C_{\bullet j} = B_{1j}A_{\bullet 1} + B_{2j}A_{\bullet 2}+\ldots+B_{nj}A_{\bullet n} = \sum_{k=1}^nA_{\bullet k}B_{kj}$.

The proof for the other part (related to rows) is similar.

---

**Proposition 1**. Let $C\in \mathbb{R}^{m\times p},A\in \mathbb{R}^{m\times n}$. Then any column of $C$ can be written as a linear combination of all the columns of $A$ if and only if $\exists B\in\mathbb{R}^{n\times p}$ such that $C=AB$.

*Proof*. Assume that any column of $C$ is a linear combination of $A$'s columns. Then 

$C_{\bullet 1} = \sum_{k=1}^n\alpha_kA_{\bullet k}\implies C_{i1} = \sum_{k=1}^n\alpha_kA_{ik}$, 
$C_{\bullet 2} = \sum_{k=1}^n\beta_kA_{\bullet k}\implies C_{i2} = \sum_{k=1}^n\beta_kA_{ik}$, 

and so on, where the implications follow from R5. Note that $(C_{\bullet r})_i = C_{ir}$ and $(A_{\bullet k})_i=A_{ik}$.

Let's re-write the coefficients corresponding to the 1st row of $C$ as $B_{k1}$ instead of $\alpha_k$. Similarly, $\beta_k$ can be re-written as $B_{k2}$, and so on, which means

$C_{i1} = \sum_{k=1}^nB_{k1}A_{ik}$, 
$C_{i2} = \sum_{k=1}^nB_{k2}A_{ik}$, 

and so on. Therefore,
$C_{ij}= \sum_{k=1}^nB_{kj}A_{ik}= \sum_{k=1}^nA_{ik}B_{kj}$

By definition of matrix product, elements $C_{ij}$ form a matrix $C=AB$. Conversely, let $C=AB$. Then
$C_{\bullet j}=\sum_{k=1}^nA_{\bullet k}B_{kj}$

by R6, and we're done.
