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

## Binomial Distribution

## Normal Distribution (Gaussian)
