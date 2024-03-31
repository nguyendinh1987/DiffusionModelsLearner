Hello world
# Start with diffusion models
- It is inspired by non-equilibrium statistical physics, is to systematically and slowly destroy structure in a data distribution through an iterative forward diffusion process. The model then learns a reverse diffusion process that restores structure in data.
- It is a probabilistic model that allows extreme flexibility in model structure, exact sampling, easy multiplication with other distributions, e.g. in order to compute a posterior, and the model log likelihood, and the probability of individual states, to be cheaply evaluated. ???
- It uses a Markov chain to gradually convert one distribution into another, an idea used in non-equilibrium statistical physics (Jarzynski, 1997) and sequential Monte Carlo (Neal, 2001).
# Diffusion process
Data distribution $q(x^{(0)})$ is gradually converted into a well behaved (analytically tractable) distribution $π(y)$ by repeated application of a Markov diffusion kernel $Tπ(y|y′; β)$ for $π(y)$, where $β$ is the diffusion rate
>> $π(y) = \int dy^{'} Tπ(y|y^{'}; β) π(y^{'})$  
>> $q(x^t|x^{t-1}) = Tπ(x^t|x^{t-1}; β)$

The forward trajectory, corresponding to starting at the data distribution and performing T steps of diffusion  

>> $q(x^{0...T})=q(x^0)\displaystyle\prod_{k=1}^T q(x^t|x^{t-1})$
# Reverse trajectory
It converts distribution $π(y)$ back to data distribution $q(x^{(0)})$ through several step of similar to diffusion process but in reverse direction
>> $π(x^T) = p(x^T)$  
>> $p(x^{0..T}) = p(x^T) \displaystyle\prod_{k=1}^T p(x^{T-1}|x^T)$

Since $q(x^t | x^{t−1})$ is a Gaussian (binomial) distribution, and if $β^t$ is small, then $p(x^{t−1} |x^t)$ will also be a Gaussian (binomial) distribution. The longer the trajectory the smaller the diffusion rate β can be made.
# Model probability
The probability the generative model assigns to the data is
>> $p(x^{(0)}) = \int dx^{1..T} p(x^{0..T})$

Naively, this integral is intractable but taking a cue from annealed importance sampling and the Jarzynski equality, we instead evaluate the relative probability of the forward and reverse trajectories, averaged over forward trajectories.

# Training??
Training amounts to maximizing the model log likelihood, which has a lower bound provided by Jensen’s inequality.  
>> $loss = \int dx^{(0)} q(x^{(0)}) log(p(x^{(0)})) \geq K$  

Training consists of finding the reverse Markov transitions which maximize this lower bound on the log likelihood (K).  
The task of estimating a probability distribution has been reduced to the task of performing regression on the functions which set the mean and covariance of a sequence of Gaussians

# Setting the diffusion rate:
The choice of $β<sub>t</sub>$ in the forward trajectory is important for the performance of the trained model. The right schedule of intermediate distributions can greatly improve the accuracy of the log partition function estimation. In thermodynamics the schedule taken when moving between equilibrium distributions determines how much free energy is lost.  

In the case of Gaussian diffusion, we learn the forward diffusion schedule β<sub>2···T</sub> by gradient ascent on K. The variance β<sub>1</sub> of the first step is fixed to a small constant to prevent overfitting. The dependence of samples from $q(x^{(1···T)} |x^{(0)})$ on β<sub>1···T</sub> is made explicit by using ‘frozen noise’.  

For binomial diffusion, the discrete state space makes gradient ascent with frozen noise impossible. We instead choose the forward diffusion schedule β<sub>1···T</sub> to erase a constant fraction $\frac{1}{T}$ of the original signal per diffusion step, yielding a diffusion rate of β<sub>t</sub> = $(T−t+1)^{-1}$ 
# Multiplying distribution and computing posteriors
# Entropy of reverse process

# Other terms:
- Model tractability and flexibility
- Monte Carlo process
- Markov chain
- non-equilibrium statistical physics
- Binominal diffusion
- Entropy
- KL divergences
- Small datasets: swiss roll, binary sequence, handwritten digit (MNIST), and several natural image as CIFAR-10, bark, and dead leaves
# References:
1. [Deep unsupervised learning using nonequilibrium thermodynamics](https://arxiv.org/pdf/1503.03585.pdf)
