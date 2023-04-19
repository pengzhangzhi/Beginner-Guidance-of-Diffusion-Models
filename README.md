[![Diffusion Models](asset/cover.png)](https://developer-blogs.nvidia.com/wp-content/uploads/2022/04/Generation-with-Diffusion-Models.png)
# Beginner Guidance of Diffusion Models

Diffusion models and score-based models have become increasingly popular in data generation for various types of media, including images and text. While these models have shown impressive performance, their heavy reliance on mathematical details can make them challenging to approach. To make the topic more accessible, I have curated a series of beginner-friendly tutorials that include both blogs and code. I hope that these resources will be useful to you in gaining a better understanding of diffusion models and their applications.

## Blogs

- Score-based models
    - https://yang-song.net/blog/2021/score/
- Diffusion Models
    - https://lilianweng.github.io/posts/2021-07-11-diffusion-models/

## Code/ notebook tutorial

- Score-based models
    - https://colab.research.google.com/drive/120kYYBOVa1i0TD85RjlEkFjaWDxSFUx3?usp=sharing#scrollTo=DfOkg5jBZcjF&uniqifier=1
- Diffusion Models
    - https://github.com/lucidrains/denoising-diffusion-pytorch
- General
    - https://github.com/sunlin-ai/diffusion_tutorial

Notably, despite their disparate foundations, diffusion models and score-based models ultimately converge to the same fundamental form. Diffusion models operate on the presumption of a Markov chain and enact a transition function that gradually incorporates noise into the data until it reaches an entirely stochastic state. Subsequently, a neural network is trained to invert this process, progressively reducing the introduced noise in each step until the original data sample is retrieved. Conversely, score-based models aim to learn the score function of a data sample, which is analogous to the gradient function of the probability density function. Once the score function is inferred, a data point can be sampled from the distribution using gradient ascent. The essence of score-based models is to approximate the score function using a neural network. During the development of score-based models, researchers discovered that the introduction of noise into the data samples significantly aids the estimation of the score function in regions of low density. This represented the first occasion where the two ostensibly distinct models exhibited subtle connections through the addition of noise.

Fascinatingly, Song demonstrated that the gradual incorporation of noise could be formulated through a stochastic differential equation (SDE), and furthermore, that diffusion models and score-based models are both special cases of SDE. To enhance the generation process, Song reformulated it by reversing the SDE, enabling SDE sampling solvers to produce high-quality samples. In addition, Song derived the associated ordinary differential equation (ODE) for an SDE, revealing connections to continuous normalizing flows. The ODE formulation provides two principal advantages. Firstly, off-the-shelf ODE solvers can be leveraged to achieve faster sampling. Secondly, the probability flow ODE formulation yields a by-product of likelihood computation.

The extraordinary potential of diffusion models and score-based models has spurred researchers to deepen their understanding of the theoretical foundations of these models and their practical applications, such as rapid sampling and the generation of diverse data modalities. However, I would like to draw attention to one area of particular interest that I believe represents the next-generation of diffusion models: probability flow ODEs. It is important to note that this class of models does not have a standardized nomenclature, and while they are referred to by a variety of names, they share common principles. Probability flow ODEs are akin to SDEs, but they formulate the data generation process as an ODE, which opens the door to one-step sampling. This is a rapidly evolving field, and I have provided a list of pertinent papers for readers to explore further.