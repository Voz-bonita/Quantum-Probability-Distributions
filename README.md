# Quantum Probability Distribution

This project is dedicated to show the intuition behind encoding probability distributions onto quantum states and implement APIs for sampling using Qiskit.

## How to build

This built on top of Qiskit. If you want to build it yourself, there is a `requirements.txt` file with all the dependencies.

`pip install -r requirements`

# Random Variables

## Bernoulli (p)

Suppose $X$ describes a random event with binary outcome, tipically $0$ or $1$. If the outcome $1$ happens with probability $p$ and the outcome $0$ happens with probability $1 - p$, i.e,

$$
P(X=x) = \begin{cases}1-p,&\text{if } x=0\\p,&\text{if } x=1\end{cases}
$$

then we say that $X\sim Bernoulli(p)$.

Thinking about qubits, we can see that this is very simillar to their behavior when performing measurement. A given qubit in state $\ket{\psi} = \begin{bmatrix}\alpha_1&\alpha_2\end{bmatrix}^{T}$, when measured will return the outcome $\ket{0}$ with probability $|{\alpha_1}|^{2}$ and $\ket{1}$ with probability $|\alpha_2|^{2}$. Due to the restriction $|{\alpha_1}|^{2} + |{\alpha_2}|^{2} = 1$, we can think of quantum states as Bernoulli random variables in the form

$$
P(\psi=x) = \begin{cases}1-|\alpha_2|^2,&\text{if } x=0\\|\alpha_2|^2,&\text{if } x=1\end{cases}\\\psi \sim Bernoulli(|\alpha_2|^2)
$$

## Binomial Distribution

## Normal Distribution (Gaussian)
