# Quantum Probability Distribution

This project is dedicated to show the intuition behind encoding probability distributions onto quantum states and implement APIs for sampling using Qiskit.

## How to build

This built on top of Qiskit. If you want to build it yourself, there is a `requirements.txt` file with all the dependencies.

`pip install -r requirements`

# Random Variables

## Bernoulli (p)

Suppose $X$ describes a random event with binary outcome, tipically $0$ or $1$. If the outcome $1$ happens with probability $p$ and the outcome $0$ happens with probability $1 - p$, i.e,

$$
P(X=x) = \begin{cases}1-p,&\text{if } x=0\\\\p,&\text{if } x=1\end{cases}
$$

then we say that $X\sim Bernoulli(p)$.

Thinking about qubits, we can see that this is very simillar to their behavior when performing measurement. A given qubit in state $\ket{\psi} = [\alpha_1~~\alpha_2]^{T}$, when measured will return the outcome $\ket{0}$ with probability $|{\alpha_1}|^{2}$ and $\ket{1}$ with probability $|\alpha_2|^{2}$. Due to the restriction $|{\alpha_1}|^{2} + |{\alpha_2}|^{2} = 1$, we can think of quantum states as Bernoulli random variables in the form

$$
P(\psi=x) = \begin{cases}1-|\alpha_2|^2,&\text{if } x=0\\\\|\alpha_2|^2,&\text{if } x=1\end{cases}
$$

$$
\psi \sim Bernoulli(|\alpha_2|^2)
$$

Now the question is how to set a quantum state to encode a desired $Bernoulli(p)$ distribution. To make things easier, let's consider the task of initializing such a quantum state, i.e., find a unitary matrix $U(p)$ such that

$$
U(p)\ket{0} = \begin{bmatrix}\alpha_1&\alpha_3\\\\\alpha_2&\alpha_4\end{bmatrix}\begin{bmatrix}1\\\\0\end{bmatrix} = \begin{bmatrix}\alpha_1\\\\\alpha_2\end{bmatrix} = \ket{\psi}
$$

$$
\psi \sim Bernoulli(p)
$$

By the definition of the $Bernoulli$ random variable, we can already conclude that our target state must have $|\alpha_2|^2 = p$ and by choosing the $\alpha_1$ and $\alpha_2$ coefficients to be positive real numbers instead of complex numbers, we conclude $\alpha_2 = \sqrt{p}$ and $\alpha_1=\sqrt{1-p}$.

Expanding the restriction that $U(p)$ must be unitary, we can determine $\alpha_3$ and $\alpha_4$.

$$
U(p)U(p)^{\dag} = \begin{bmatrix}\sqrt{1-p}&\alpha_3\\\\\sqrt{p}&\alpha_4\end{bmatrix}\begin{bmatrix}\sqrt{1-p}&\sqrt{p}\\\\\bar{\alpha}_3&\bar{\alpha}_4\end{bmatrix} = \begin{bmatrix}1&0\\\\0&1\end{bmatrix}
$$

$$
\begin{cases}1-p + \alpha_3\bar{\alpha}_3 &= 1\\\\\sqrt{p}\sqrt{1-p} + \alpha_3\bar{\alpha_4} &= 0\\\\\sqrt{p}\sqrt{1-p} + \alpha_4\bar{\alpha}_3 &= 0\\\\p + \alpha_4\bar{\alpha_4} & = 1\end{cases}
$$

The first equation in the system could be easily made true if $\alpha_3 = \pm\sqrt{p}$. Suppose we pick $\alpha_3 = -\sqrt{p}$, then the second equation in the system states that $\bar{\alpha}_4 = \sqrt{1 - p}$. Since we picked real coefficients for every $\alpha$, we've already determined the matrix $U(p)$ and it's conjugate transpose, now it is just a matter of checking it satisfies the third and fourth equation, that is

$$
\sqrt{p}\sqrt{1-p} - \sqrt{p}\sqrt{1-p} = 0
$$

$$
p + \sqrt{1-p}\sqrt{1-p} = p + 1 - p = 1,
$$

concluding that

$$
U(p) = \begin{bmatrix}\sqrt{1-p}&-\sqrt{p}\\\\\sqrt{p}&\sqrt{1-p}\end{bmatrix}
$$

## Binomial Distribution

## Normal Distribution (Gaussian)
