---
title: Berry Phase
draft: false
tags:
  - Quantum Mechanics
---

The general definition of the Berry phase is a phase angle (from 0 to $2\pi$) that a complex vector acquires as it is transported through a path in its complex vector space. The idea was popularized by Sir Michael Berry in 1984.

To demonstrate the Berry phase, we consider some state in Hilbert space (e.g. the ground state) of some system parameterized by a continuously varying parameter (e.g magnetic field, nuclear coordinates etc.). We then vary the parameter in a closed path, such that the system returns to where it started. 
## Adiabatic Approximation
If the parameters very "slowly" with time, then energy eigenvalues should just follow the change in parameters. The eigenvectors will acquire an additional geometrical phase associated with the change in parameter. 

Assuming no degeneracy (so as to have constant ordering of states),the energy eigenstates are found from the time-independent Schrodinger equation
$$
H(t) |n; t\rangle = E_n (t) |n; t\rangle
$$
noting that at any time $t$, the states and eigenvalues may change. The time-dependent Schrodinger equation for some arbitrary ket expanded in the energy eigenstates is
$$
	i\hbar \frac{\partial}{\partial t} |\alpha; t \rangle = H(t) |\alpha; t \rangle
$$
where 
$$
|\alpha; t \rangle = \sum_{n} c_n (t) e^{i \theta_n(t)} |n; t \rangle
$$
and $\theta(t)$ is the typical dynamical phase acquired by the energy eigenstates
$$
	\theta_n (t) = -\frac{1}{\hbar} \int_0 ^t E_n(t') dt'
$$
Through a straightforward substitution into the TDSE, taking the time-derivative of the TDSE, acting from the left with an equal time eigenstate, and using orthogonality of equal time eigenstates, one arrives at a differential equation for the coefficients,
$$
\dot{c}_m(t) = -c_m(t) \langle m;t| \frac{\partial}{\partial t}|m; t\rangle - \sum_{n} c_n(t) e^{i(\theta_n - \theta_m)} \frac{\langle m;t| \dot{H} | n;t\rangle}{E_n(t) - E_m(t)}
$$
The second term shows mixing with other states due to the time dependence of the Hamiltonian. This result is exact. The adiabatic approximation amounts to neglecting the second term, meaning 
$$
\frac{\langle m;t| \dot{H} | n;t\rangle}{E_n(t) - E_m(t)} \equiv\frac{1}{\tau} \ll \langle m;t| \frac{\partial}{\partial t}|m; t\rangle \approx \frac{E_m}{\hbar}
$$
The solution for the coefficients is then

## Discrete formulation
Consider N vectors $|u_0\rangle$ to $|u_{N-1}\rangle$ that describe the ground state of a system at each discrete step in parameter space, where the last state $|u_{N}\rangle$ is identified with $|u_{0}\rangle$. The Berry phase is _defined_ as 
$$
\phi = -Im \ ln[ \langle u_0 | u_1 \rangle\langle u_1|u_2 \rangle \cdots\langle u_{N-1}|u_0 \rangle]
$$
The reason for the imaginary natural log is that for some complex number $z = |z| e^{i\phi}$, $Im\ ln z = \phi$ , so we only retain the information about its phase. This definition chooses a branch of $Im \ ln\ z$ such that $-\pi < \phi \leq \pi$. The minus sign is conventional. This formulation has the benefit that it is gauge independent. 

### Parallel-Transport Gauge

We are free to choose any gauge we like for each of the $|u_j\rangle$ . We can define new gauges s.t. $|\bar{u}_0\rangle = |u_0\rangle$ , then choose the phase of $|u_1\rangle$ such that $\langle \bar{u}_0 | \bar{u}_1\rangle$ is real and positive. If we propagate this down the line of states, then 
$$
\text{Im}\ \text{ln} \langle \bar{u}_j | \bar{u}_{j+1}\rangle = 0
$$
This generates what is known as the parallel transport gauge. In this gauge choice,$|\bar{u}_0 \rangle$ is no longer equivalent to  $|\bar{u}_N \rangle$, and they differ by exactly the Berry phase
$$
\phi = \text{Im}\ \text{ln} \langle \bar{u}_N | \bar{u}_{0}\rangle
$$
The phase difference of the states are exactly zero until an abrupt discontinuity at the end of the loop. 

### Twisted Parallel-Transport Gauge
We may like to have a choice of phase that is continuous throughout the evolution of the state. 