## Linear Algebra for ML
**Notation**: The set of all $m\times n$ real matrices will be denoted by $\mathbb{R}^{m\times n}$. The $i$-th column of a matrix $A$ will be denoted by $A_{i\bullet}$. The $j$-th column will be denoted by $A_{\bullet j}$.

---
**Very important results [memorize].**

**R1**. Let $A\in\mathbb{R}^{m\times n}, B\in\mathbb{R}^{n\times p}$. Then $(AB)_{\bullet j}=AB_{\bullet j}$.

*Proof*. $(AB)_{ij} = \sum_{k=1}^n A_{ik}B_{kj} \implies (AB)_{\bullet j} = \sum_{k=1}^n A_{\bullet k}B_{kj}$

---
Proposition 1. Let $C\in \mathbb{R}^{m\times p},A\in \mathbb{R}^{m\times n}$. Then *any* column of $C$ can be written as a linear combination of *all* the columns of $A$ if and only if $\exists B\in\mathbb{R}^{n\times p}$ such that $C=AB$.

*Proof*. 
