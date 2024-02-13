*This project contains code, visualisations, and datasets for a two-spin Ising magnet model using Glauber (spin flip) and Kawasaki (spin swap) dynamics.*

## Ising Model of a Magnet
The Ising model comprises $N$ spins $S_i$ on a lattice (so that $i$ = 1, ... , $N$), each of which can point up, $S_i = 1$, or down, $S_i = −1$. Each neighbouring pair of aligned spins lowers the energy of the system by an amount $J > 0$. Thus, given a spin configuration $\set{S_i}$, the total energy is
$$E({Si}) = −J \sum_{\{i, j\}} S_i S_j$$
where the sum is over all distinct nearest neighbour pairs $\{i, j\}$. According to the Boltzmann distribution, that probability of observing a given configuration $\set{S_i}$ at equilibrium is
$$P(\set{S_i}) = \exp (−E(\set{S_i})/(k_B T)) $$
where $k_B$ is Boltzmann’s constant and $T$ is the temperature. Note that since the physics of the system is determined by the ratio between $J$ and $k_B T$ (which enters the Boltzmann weight), we can take any two of $J$, $k_B$ and $T$ equal to unity with no loss of generality – in practice calculations normally have $J = k_B = 1$. Of course, setting $J = kB = T = 1$ does lose generality.

The two models implemented here are Glauber dynamics (where at each iteration a random spin is chosen and a flip attempt is made) and Kawasaki dynamics (where at each iteration an attempt is made to swap two random spins). A change in the system's energy is calculated and a new state is accepted with a probability $p = \min \set{1, \exp(\Delta E / k_b T)}$. This is known as the Metropolis test. 

### Glauber Dynamics
![anim-glauber200](https://github.com/jakub-maly/Ising-Models/assets/50239149/f48f05c2-8994-4c79-a8d0-1bdbed8f16d5)

### Kawasaki Dynamics
![anim-kawasaki200](https://github.com/jakub-maly/Ising-Models/assets/50239149/4b4a0a45-c27a-4646-b56c-a1e234473296)
(Note that since Kawasaki dynamics preserve the number of spin states, the total magnetisation of a Kawasaki system remains constant.)


## Magnetisation & Heat Capacity
The total magnetisation of a configuration $\set{S_i}$ is defined as $M = \sum_i S_i$. We can use the program to estimate the average value of the total magnetisation in the equilibrium state, $\langle M \rangle$, and of the susceptibility
$$\chi = \frac{1}{Nk_bT} (\langle M^2 \rangle - \langle M \rangle ^2)$$
as a function of temperature $T$, as shown below. We can use these graphs to estimate the location of the critical temperature at which the system spontaneously magnetises under Glauber dynamics.

We can also look at the average of the total energy, $\langle E \rangle$, and the scaled heat capacity (or heat capacity per spin)
$$C_V = \frac{1}{Nk_bT^2} (\langle E^2 \rangle - \langle E \rangle ^2)$$
and plot these quantities as a function of $T$ (including errors) to estimate the critical temperature.

![plot-energy_and_magnetisation](https://github.com/jakub-maly/Ising-Models/assets/50239149/9f773878-1f12-4979-942b-0e80b0b98008)
![plot-heat_capacity_and_susceptibility](https://github.com/jakub-maly/Ising-Models/assets/50239149/88cd20ee-7ea6-4641-b2d7-c1d333f4e786)

From the plots above, we can see that the critical temperature is around $T_c = 2.3$, with Glauber dynamics exhibiting a more defined critical point.
