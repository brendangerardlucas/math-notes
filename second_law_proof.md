# Simple proof of the second law of thermodynamics that uses the Kullback-Leibler divergence.

## Brendan Lucas
Consider an isolated thermodynamic system a random discrete energy variable $E$. The first law of thermodynamics states that the internal energy $U = \langle E \rangle = \sum_i p_i E_i$ is constant in an isolated system. The system may start in a nonequilibrium state, but it approaches an equilibrium state $p_i = \frac{e^{-\beta E_i}}{\sum_j e^{-\beta E_j}}$. We consider the set of discrete energy levels $\mathcal{E}\ni E_i$ not to change in time, and the temperature of the system to be a constant $\beta = k_B T$.

$p_{\text{now}}$ is our model of the system's energy now, and $p_{\text{eq}}$ is the unique marginal of $\mathcal{E}$'s equilibrium; $p_{\text{eq}}$ is "the heat death of the universe." $\beta=1/k_BT$ is inverse temperature, or coldness. $p_{\text{now}}$ is compared against $p_{\text{eq}}$ with the Kullback-Leibler divergence (KLD). $p_{\text{now}}$ can be any marginal over $\mathcal{E}$, 1. Define KLD:

$$D[p_{\text{now}}\|p_{\text{eq}}] = \sum_{i=1}^N p_{\text{now}}(E_i)\ln\left(\frac{p_{\text{now}}(E_i)}{p_{\text{eq}}(E_i)}\right) = \sum_{i=1}^N p_{\text{now}}(E_i)\ln p_{\text{now}}(E_i) -\sum_{i=1}^N p_{\text{now}}(E_i)\ln p_{\text{eq}}(E_i)$$
2. Expand and add a special zero
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \sum_{i=1}^N p_{\text{now}}(E_i)\ln p_{\text{now}}(E_i) -\sum_{i=1}^N p_{\text{now}}(E_i)\ln p_{\text{eq}}(E_i) \\
&+\left(\sum_{i=1}^N p_{\text{eq}}(E_i)\ln p_{\text{eq}}(E_i) - \sum_{i=1}^Np_{\text{eq}}(E_i)\ln p_{\text{eq}}(E_i) \right)  \\
\end{aligned}
$$
3. Convert to macroscopic variables with $\frac{1}{k_B}S=-\sum_{i=1}^N p_i\ln p_i$
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \frac{1}{k_B}\Delta S-\sum_{i=1}^N p_{\text{now}}(E_i)\ln p_{\text{eq}}(E_i) \\
&+\sum_{i=1}^N p_{\text{eq}}(E_i)\ln p_{\text{eq}}(E_i)  \\
&= \frac{1}{k_B}\Delta S + \sum_{i=1}^N [p_{\text{eq}}(E_i)-p_{\text{now}}(E_i)]\ln p_{\text{eq}}(E_i)
\end{aligned}
$$
4. Plug in the "heat death" partition function: $p_{\text{eq}}(E_i) = \frac{e^{-\beta E_i}}{\sum_{j=1}^Ne^{-\beta E_j}} = \frac{e^{-\beta E_i}}{Z}$,
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \frac{1}{k_B}\Delta S + \sum_{i=1}^N [p_{\text{eq}}(E_i)-p_{\text{now}}(E_i)]\ln\left(\frac{e^{-\beta E_i}}{\sum_{j=1}^Ne^{-\beta E_j}}\right)\\
&= \frac{1}{k_B}\Delta S + \sum_{i=1}^N [p_{\text{now}}(E_i)-p_{\text{eq}}(E_i)]\cdot [\beta E_i] + \sum_{i=1}^N [p_{\text{now}}(E_i)-p_{\text{eq}}(E_i)]\ln Z
\end{aligned}
$$
5. Notice that
$$\sum_{i=1}^N [p_{\text{now}}(E_i)-p_{\text{eq}}(E_i)]\ln Z = \ln Z [\sum_{i=1}^Np_{\text{now}}(E_i)-\sum_{i=1}^Np_{\text{eq}}(E_i)] = \ln Z - \ln Z = 0$$
So, 
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \frac{1}{k_B}\Delta S + \sum_{i=1}^N [p_{\text{now}}(E_i)-p_{\text{eq}}(E_i)]\cdot [\beta E_i]
\end{aligned}
$$
6. The following step gives a difference in the expectation values of energy if and only if every $E_i$ is the same in $p_{\text{eq}}$ and $p_{\text{now}}$; the energy levels did not change, but only their probabilities changed. 
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \frac{1}{k_B}\Delta S + \sum_{i=1}^N p_{\text{now}}(E_i)\beta E_i-\sum_{i=1}^N p_{\text{eq}}(E_i)\beta E_i \\
&= \frac{1}{k_B}\Delta S -\beta\Delta \langle E \rangle
\end{aligned}
$$
7. Internal energy $U=\langle E \rangle$ is a constant,

$$k_B D[p_{\text{now}}\|p_{\text{eq}}] = \Delta S,$$

8. KLD is non-negative, so

$$\Delta S\geq 0$$

QED, that is the second law of thermodynamics. **The entropy of an isolated thermodynamic system can only increase or stay the same, but never decrease!**
