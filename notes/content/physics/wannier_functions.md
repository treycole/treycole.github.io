---
title: Wannier Functions
draft: false
tags:
  - Physics
  - Condensed Matter
---

Wannier functions are the localized representation of the Bloch energy eigenstates of a periodic crystal. They effectively are related to a given Bloch energy eigenstate through a Fourier transform
$$
\begin{align}
|w_{n\vec{R}}\rangle &= \frac{V_{cell}}{(2\pi)^3} \int_{BZ} e^{-i\vec{k}\cdot\vec{R}}\ |\psi_{n\vec{k}}\rangle d^3k \\
|\psi_{n, \vec{k}} \rangle &= \sum_{\vec{R}}e^{i\vec{k}\cdot\vec{R}}\ |w_{n, 
\vec{k}} \rangle
\end{align}
$$
As long as the Bloch eigenstates are a smooth function of $\vec{k}$, then the Wannier representation decays rapidly with $|\vec{r} -\vec{R}|$  for some given $\vec{R}$ associated with the Wannier state. 

The Fourier transform is a special case of a unitary transformation, so we can view the Bloch and Wannier functions as providing two different bases describing the same manifold of states associated with an energy band. Another way of saying this is that the projector onto band $n$ is unitarily equivalent,
$$
\mathcal{P}_n = \frac{V_{cell}}{(2\pi)^3} \int_{BZ} |\psi_{n\vec{k}}\rangle\langle \psi_{n\vec{k}}| d^3k = \sum_{\vec{R}} |w_{n\vec{R}}\rangle \langle w_{n\vec{k}}|
$$
### Multiple Bands
The assumption that the Bloch eigenstates are smooth and periodic in $\vec{k}$ is based on the assumption that there are no degeneracies. However this is uncommon, there are typically degeneracies at high-symmetry points in the BZ. We can instead consider a group of $J$ ordered bands that are separated by a finite energy gap from other bands. In insulators, the set of bands non-degenerate with the complementary set of bands will typically be the occupied band subspace. What we then seek is a set of $J$ Wannier functions spanned by the $J$ Bloch eigenstates constructed as,
$$
|w_{n,\vec{R}}\rangle = \frac{V_{cell}}{(2\pi)^3}\int_{BZ}e^{-i\vec{k}\cdot\vec{R}}
|\tilde{\psi}_{n, \vec{k}}\rangle\  d^3k
$$
where the $|\tilde{\psi}_{n, \vec{k}}\rangle$ are smooth functions of $\vec{k}$ everywhere in the BZ that are related to the true Bloch energy eigenstates via a unitary transform
$$
|\tilde{\psi}_{n\vec{k}}\rangle = \sum_{m=1}^{J}U_{mn}(\vec{k})|\psi_{m, \vec{k}}\rangle
$$
The manifold of $J \times J$ unitary matrices $U_{mn}(\vec{k})$ have been chosen to "iron out" the non-analytic behavior near the degeneracies at high symmetry points. Then, the Wannier functions will be exponentially localized. The cell-periodic wavefunctions $|u_{n,\vec{k}}\rangle$ transform in the same way as the Bloch eigenstates,
$$
|\tilde{u}_{n\vec{k}}\rangle = \sum_{m=1}^{J} U_{mn}(\vec{k}) |u_{m\vec{k}}\rangle
$$
This is known as a _multiband_ or _non-Abelian_ gauge transformation. It is not obvious whether this procedure is always possible. It can always be accomplished in localized region around some $\vec{k_0}$, where we choose a set $|\tilde{u}_{n\vec{k}}\rangle$ of orthonormal functions spanning the band subspace of $H_{\vec{k_0}}$, being either the eigenstates themselves or some unitary rotation of them. We then choose at each nearby $\vec{k}$ a unitary rotation on the energy eigenstates $|u_{n\vec{k}}\rangle$  such that they are "optimally aligned" with $|\tilde{u}_{n\vec{k_0}}\rangle$. 
##### Optimal Alignment 
Given two sets of orthonormal sets of $J$  states $|u_n\rangle$ and $|\nu_n\rangle$, where the subspaces  $\mathcal{P}_u = \sum |u_n\rangle \langle u_n |$ and $\mathcal{P}_{\nu} = \sum |\nu_n\rangle \langle \nu_n|$ spanned by these states are similar but not identical. We would like to rotate one set such that they are as similar to the other as possible in both phase and character. 

Optimal alignment occurs when 
$$
\tilde{M}_{mn} = \langle u_m| \tilde{v}_n \rangle
$$
is as close to the unit matrix as possible. Initially, before the unitary rotation,
$$
M_{mn} = \langle u_m | \nu_n \rangle
$$
We then perform a SVD on $M$ 
$$
M = V\Sigma W^{\dagger}
$$
where $V$ and $W$ are $J\times J$ unitary matrices and $\Sigma_{mn} = s_n \delta_{nm}$ is a diagonal matrix whose elements $s_n \in \mathcal{R} \gt 0$ are called "singular values". One can show that if we apply $V$ to the set of states $\{ |u_n\rangle \}$ and $W$ to the set of states $\{ |\nu_n\rangle \}$ we get new states
$$
\begin{align}
|u'_n \rangle &= \sum_m V_{mn} |u_m\rangle \\
|\nu'_n \rangle &= \sum_m W_{mn} |\nu_m\rangle
\end{align}
$$
that are optimally aligned in the sense that 
$$
M' = \langle u'_m | \nu'_n \rangle = s_n \delta_{mn}
$$
The extent to which $s_n \lt 1$ is a measure of the difference between $\mathcal{P}_u$ and $\mathcal{P}_{\nu}$. Since we are given $|u_n\rangle$ and they shouldn't be rotated, we apply $V^{\dagger}$ to both sets, returning $|u'_n \rangle$ back to $|u_n\rangle$ and 
$$
|\tilde{\nu}_n\rangle = \sum_m (WV^{\dagger})_{mn} | \nu_m \rangle
$$
which are in optimal alignment with the initial $|u_n\rangle$. We also can think about the procedure as constructing the best unitary approximation to $M$ 
$$
\mathcal{M} = VW^{\dagger}
$$
that tells us how the states $|u_n\rangle$ got rotated in going to the $|\nu_n\rangle$. We then apply the h.c. to undo this rotation. If any of the $s_n = 0$ than there is a subspace of vectors in $\mathcal{P}_{\nu}$ that are orthogonal to the space spanned by $\mathcal{P}_u$ so they can't be aligned. 

##### Projection method
The procedure of optimal alignment works locally in $k$ but whether there is always a way to do this globally is highly non-trivial. One way of practically constructing multiband Wannier functions is via the _projection method_. 
- Choose a set of $J$ localized "trial functions" $|t_n \rangle$ whose locations and characters are similar to the expected Wannier functions
- Expand this set of functions to include periodic images $|t_{n\vec{R}}\rangle$ and construct Bloch like functions $|\chi_{n\vec{k}}\rangle = \sum_{\vec{R}} e^{i\vec{k}\cdot\vec{R}} |t_{n\vec{R}}\rangle$ that are smooth in $\vec{k}$ 
- Orthonormalize them at each $\vec{k}$ via computing the overlap matrix $S^{(\vec{k})}_{mn} = \langle \chi_{m\vec{k}} | \chi_{n\vec{k}}\rangle$ and construct $|\chi'_{n\vec{k}}\rangle = \sum_m (S_{\vec{k}}^{-1/2})_{mn} |\chi_{m \vec{k}}\rangle$ 
- Perform $J\times J$ unitary rotation on the $|\psi_{n\vec{k}}\rangle$ so as to obtain $|\tilde{\psi}_{n\vec{k}}\rangle$ that are optimally aligned with the $|\chi'_{n\vec{k}}\rangle$ using the optimal alignment 
For some choices of trial functions, $|\chi_{n\vec{k}}\rangle$ are not linearly independent and $S_{\vec{k}}$ becomes singular and the procedure fails. For ordinary insulators, the procedure can be fixed via a new choice of trial function. In certain kinds of topological insulators, there can be a [[topological_obstructions|topological obstruction]]; in this case a singularity in $S_{\vec{k}}$ is gauranteed to occur somewhere in the BZ.

### Localization


### Wannier interpolation