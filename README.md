[![Diffusion Models](asset/cover.png)](https://developer-blogs.nvidia.com/wp-content/uploads/2022/04/Generation-with-Diffusion-Models.png)
# Beginner Guidance of Diffusion Models

<details>
<summary>Introduction in Chinese</summary>
扩散模型和基于分数的模型在生成各种类型的媒体数据，包括图像和文本方面越来越受欢迎。虽然这些模型表现出了惊人的性能，但它们严重依赖于数学细节，可能难以入手。为了使这个主题更易于理解，我精选了一系列适合初学者的教程，包括博客和代码。我希望这些资源能够帮助你更好地理解扩散模型及其应用。

</details>
Diffusion models and score-based models have become increasingly popular in data generation for various types of media, including images and text. While these models have shown impressive performance, their heavy reliance on mathematical details can make them challenging to approach. To make the topic more accessible, I have curated a series of beginner-friendly tutorials that include both blogs and code. I hope that these resources will be useful to you in gaining a better understanding of diffusion models and their applications.

## Blogs

- Score-based models
    - https://yang-song.net/blog/2021/score/
- Diffusion Models
    - https://lilianweng.github.io/posts/2021-07-11-diffusion-models/

## Code & notebook tutorial

- Score-based models
    - https://colab.research.google.com/drive/120kYYBOVa1i0TD85RjlEkFjaWDxSFUx3?usp=sharing#scrollTo=DfOkg5jBZcjF&uniqifier=1
- Diffusion Models
    - https://github.com/lucidrains/denoising-diffusion-pytorch
- General
    - https://github.com/sunlin-ai/diffusion_tutorial
    
## Application
- Protein generation
    - [se(3) Diffusion](https://arxiv.org/pdf/2302.02277.pdf), [Code](https://github.com/jasonkyuyim/se3_diffusion)

## Disscusion

<details>
<summary>Chinese (translated by ChatGPT)</summary>
值得注意的是，尽管扩散模型和基于分数的模型具有不同的基础，但它们最终收敛到相同的基本形式。扩散模型基于马尔可夫链的假设，并执行过渡函数，逐渐将噪声引入数据，直到达到完全随机的状态。随后，训练神经网络以反转此过程，逐步在每个步骤中减少引入的噪声，直到检索到原始数据样本。相反，基于分数的模型旨在学习数据样本的分数函数，这类似于概率密度函数的梯度函数。一旦推断出分数函数，可以使用梯度上升从分布中对数据点进行采样。基于分数的模型的本质是使用神经网络来逼近分数函数。在开发基于分数的模型期间，研究人员发现将噪声引入数据样本可极大地帮助在低密度区域估计分数函数，这是两个表面上不同的模型通过添加噪声展示微妙联系的首次机会。

有趣的是，Song表明，逐渐引入噪声可以通过随机微分方程（SDE）来制定，并且扩散模型和基于分数的模型都是SDE的特殊情况。为了增强生成过程，Song通过反转SDE重构了它，使SDE采样求解器能够生成高质量的样本。此外，Song推导出了SDE的相关常微分方程（ODE），揭示了与连续归一化流的联系。ODE公式提供了两个主要优势。首先，可以利用现成的ODE求解器实现更快的采样。其次，概率流ODE公式产生了可能性计算的副产品。

扩散模型和基于分数的模型的非凡潜力促使研究人员深入了解这些模型的理论基础和实际应用，例如快速采样和生成多样化的数据模态。然而，我想引起特别关注的一个领域是我认为代表扩散模型下一代的概率流ODE。值得注意的是，这类模型没有标准化的术语，虽然它们被称为各种名称，但它们具有共同的原则。概率流ODE类似于SDE，但它将数据生成过程制定为ODE，这打开了一步采样的大门。这是一个快速发展的领域，我为读者提供了一些相关的论文以供进一步学习。

</details>


Notably, despite their disparate foundations, diffusion models and score-based models ultimately converge to the same fundamental form. Diffusion models operate on the presumption of a Markov chain and enact a transition function that gradually incorporates noise into the data until it reaches an entirely stochastic state. Subsequently, a neural network is trained to invert this process, progressively reducing the introduced noise in each step until the original data sample is retrieved. Conversely, score-based models aim to learn the score function of a data sample, which is analogous to the gradient function of the probability density function. Once the score function is inferred, a data point can be sampled from the distribution using gradient ascent. The essence of score-based models is to approximate the score function using a neural network. During the development of score-based models, researchers discovered that the introduction of noise into the data samples significantly aids the estimation of the score function in regions of low density. This represented the first occasion where the two ostensibly distinct models exhibited subtle connections through the idea of addition of noise.

Fascinatingly, Song demonstrated that the gradual incorporation of noise could be formulated through a stochastic differential equation (SDE), and furthermore, that diffusion models and score-based models are both special cases of SDE. To enhance the generation process, Song reformulated it by reversing the SDE, enabling SDE sampling solvers to produce high-quality samples. In addition, Song derived the associated ordinary differential equation (ODE) for an SDE, revealing connections to continuous normalizing flows. The ODE formulation provides two principal advantages. Firstly, off-the-shelf ODE solvers can be leveraged to achieve faster sampling. Secondly, the probability flow ODE formulation yields a by-product of likelihood computation.

The extraordinary potential of diffusion models and score-based models has spurred researchers to deepen their understanding of the theoretical foundations of these models and their practical applications, such as rapid sampling and the generation of diverse data modalities. However, I would like to draw attention to one area of particular interest that I believe represents the next-generation of diffusion models: probability flow ODEs. It is important to note that this class of models does not have a standardized nomenclature, and while they are referred to by a variety of names, they share common principles. Probability flow ODEs are akin to SDEs, but they formulate the data generation process as an ODE, which opens the door to one-step sampling. This is a rapidly evolving field, and I have provided a list of pertinent papers for readers to explore further.


