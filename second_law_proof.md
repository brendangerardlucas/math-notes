# Five axioms are required for a proof of the second law of thermodynamics that uses the Kullback-Leibler divergence.

## Brendan Lucas
Consider a physical universe with random, discrete, generalized[^1] energy $E$. The second law follows from these five axioms:

**Axiom 1.** Energy is a discrete random variable $E$ in a sample space $\mathcal{E}\ni E_i\forall i$ with marginal probability $p(E)$[^2].

**Axiom 2.**  The expected energy $\langle E \rangle=\sum_i p_i E_i$ of the universe is a constant.

**Axiom 3:** If the universe is not in an equilibrium, it will be in equilibrium.

**Axiom 4:** The set of all energies $\mathcal{E}$ does not change, even as the distribution $p(E)$ may change. In other words, $\mathcal{E}$ is invariant.
 
**Axiom 5:** The temperature of the universe is a constant.

You may not be inclined to accept these axioms as a physical reality. Certainly, they are dubious. But they are also inuitive; Axiom 1 mirrors the insights of quantum mechanics, Axiom 2 mirrors what we call the first law of thermodynamics (which we need not assume its traditional form), Axiom 3 almost constitutes the very definition of equilibrium, and Axiom 4 establishes energy as something objective, while the (apparently Bayesian) probabilities can be subjective. Axiom 5, I will not deny, is almost certainly false.

"Proof" of these axioms is out of scope; they may all be false. But we show they are sufficient to prove the second law of thermodynamics, so that is special about them. "Fluctuation theorems" only come so close; they only show an *expectation value* of a change in entropy to be non-negative, not the change in entropy itself.[^3]


"Statistical mechanics," as it is commonly understood, we call "the equilibrium theory." This is because "The generalized Boltzmann distribution $p_{\text{eq}}(E_i) = \frac{e^{-E_i/k_B T}}{\sum_j e^{-E_j/k_B T}}$ is the only distribution for which the Gibbs-Shannon entropy $H = -\sum_i p_i\ln p_i$ is equal to the thermodynamic entropy $S=k_B H$. (Gao 2019 [https://arxiv.org/abs/1903.02121])" The generalized Boltzmann distribution *is* the maximum entropy distribution, the equilibrium distribution, so we call it $p_{\text{eq}}$. Away from equilibrium (that is to say, *in real life*), thermodynamic entropy[^4] has not been demonstrated to have statistical definition[^5]. They won't tell you that in school! But for this derivation, we concern ourselves solely with the Gibbs-Shannon entropy, and do not worry about different thermodynamic entropies or generalized entropies such as those of Tsallis or Renyi.

$p_{\text{now}}$ is our model of the universe's energy now, and $p_{\text{eq}}$ is the unique marginal of $\mathcal{E}$'s equilibrium; $p_{\text{eq}}$ is "the heat death of the universe." $\beta=1/k_BT$ is inverse temperature, or coldness of the universe. $p_{\text{now}}$ is compared against $p_{\text{eq}}$ with the Kullback-Leibler divergence (KLD). $p_{\text{now}}$ can be any marginal over $\mathcal{E}$, including the equilibrium distribution (but hopefully not, if one likes to live). *The fourth axiom is required to define the KLD*.

1. Define KLD:
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
6. The following step gives a difference in the expectation values of energy if and only if every $E_i$ is the same in $p_{\text{eq}}$ and $p_{\text{now}}$; axiomatically, the energy levels did not change, but only their probabilities changed. 
$$
\begin{aligned}
D[p_{\text{now}}\|p_{\text{eq}}] &= \frac{1}{k_B}\Delta S + \sum_{i=1}^N p_{\text{now}}(E_i)\beta E_i-\sum_{i=1}^N p_{\text{eq}}(E_i)\beta E_i \\
&= \frac{1}{k_B}\Delta S -\beta\Delta \langle E \rangle
\end{aligned}
$$
7. Invoke the second axiom,

$$k_B D[p_{\text{now}}\|p_{\text{eq}}] = \Delta S,$$

8. KLD is non-negative, so

$$\Delta S\geq 0$$

QED, that is the second law of thermodynamics, in all the glory of its shaky foundation. **The entropy of a universe with these five axioms can only increase or stay the same, but never decrease!**

[^1]: You may prefer one related to enthalpy, $E_i = \varepsilon_i + pV_i$, or involve a chemical potential like $E_i = \varepsilon_i \pm \mu N_i$, where $\varepsilon_i$ is defined so that $\sum_{i} p_i \varepsilon_i = U$ is the internal energy, or something else. The math works out the same, but the exact expression of the (generalized) free energy will be different. Henceforth "generalized energy" is just "energy."

[^2]:$p(E)$ describes the frequency at which different values of $E$ can be observed, or assigns a degree of subjective belief to each possible energy level.

[^3]: "Whither Time's Arrow?" by Gavin E. Crooks


[^4]: "Thermodynamic entropy" is entropy as it was understood by Clausius and Kelvin, or now by chemists and some (e.g. mechanical) engineers.

[^5]: "Gibbs-Shannon entropy" is the definition preferred by many theorists and other (e.g. electrical) engineers.
