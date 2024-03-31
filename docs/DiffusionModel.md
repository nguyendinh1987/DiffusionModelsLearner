Hello world
# Start with diffusion models
- It is inspired by non-equilibrium statistical physics, is to systematically and slowly destroy structure in a data distribution through an iterative forward diffusion process. The model then learns a reverse diffusion process that restores structure in data.
- It is a probabilistic model that allows extreme flexibility in model structure, exact sampling, easy multiplication with other distributions, e.g. in order to compute a posterior, and the model log likelihood, and the probability of individual states, to be cheaply evaluated. ???
- It uses a Markov chain to gradually convert one distribution into another, an idea used in non-equilibrium statistical physics (Jarzynski, 1997) and sequential Monte Carlo (Neal, 2001).
# Diffusion process
>> x^y
# Reverse trajectory
# Model probability
# Training and evaluation
# Multiplying distribution and computing posteriors
# Entropy of reverse process

# Other terms:
- Model tractability and flexibility
- Monte Carlo process
- Markov chain
- non-equilibrium statistical physics
- Small datasets: swiss roll, binary sequence, handwritten digit (MNIST), and several natural image as CIFAR-10, bark, and dead leaves
# References:
1. [Deep unsupervised learning using nonequilibrium thermodynamics](https://arxiv.org/pdf/1503.03585.pdf)
