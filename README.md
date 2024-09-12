
# Diffusion Models with Alternative Noising Distributions and Schedules

This project, led by [Ron Taieb](https://www.linkedin.com/in/ron-taieb-7991231bb/) and [Ori Meidler](https://www.linkedin.com/in/ori-meidler/), explores diffusion models by extending the traditional setup with alternative noise distributions and scheduling strategies. We focus on generating data from known distributions, experimenting with Gaussian Mixture Models (GMM) and Gamma distributions alongside the Gaussian noise typically used in diffusion models.
We also explore sigmoid scheduling in comparison to cosine scheduling and experiment with a new dynamic scheduling framework.


## Table of Contents
- [Introduction](#introduction)
- [Noise Distributions](#noise-distributions)
- [Scheduling Approaches](#scheduling-approaches)
- [Results and Evaluation](#results-and-evaluation)
- [Future Work](#future-work)

## Introduction

Diffusion models, introduced by Sohl-Dickstein et al. (2015), have transformed generative AI by learning a reverse process to reconstruct data from noise. This project extends the OpenAI model (Dhariwal & Nichol, 2021) to new noising distributions like GMM and Gamma, based on the work of Nachmani et al. (2021). We also explore noise scheduling techniques, focusing on cosine and sigmoid scheduling.


## Noise Distributions

The project explores different noise distributions beyond the typical Gaussian distribution:
- **Gaussian Mixture Model (GMM)**
- **Gamma Distribution**

## Scheduling Approaches

We experiment with three main scheduling methods:
- **Cosine Schedule**: A smooth function that introduces noise gradually.
- **Sigmoid Schedule**: Similar to the cosine schedule, but with slower noise introduction in the early steps and faster toward the end.
- **Dynamic Schedule**: Built on the cosine schedule, it adjusts beta over epochs to improve results.
  
## Results and Evaluation

The performance of each method was evaluated using Kullback-Leibler (KL) divergence between the generated data and the true data. The results for different scheduling methods and noise types can be seen below:

| Scheduling Method  | Noise Distribution  | KL Divergence |
|--------------------|---------------------|--------------|
| **Cosine**         | GMM                 | 0.1226       |
| **Cosine**         | Gaussian            | 0.0765       |
| **Cosine**         | Gamma               | 0.2856       |
| **Sigmoid**        | GMM                 | 0.0831       |
| **Sigmoid**        | Gaussian            | 0.0733       |
| **Sigmoid**        | Gamma               | 0.8999       |

Additionally, we compared the performance of the dynamic cosine scheduling against the standard cosine scheduling using the Gaussian noise distribution. Here are the results:

| Scheduling Method    | Limit Distribution  | KL Divergence |
|----------------------|---------------------|--------------|
| **Cosine**           | Gaussian            | 0.0765       |
| **Dynamic Cosine**    | Gaussian            | 0.0699       |


## Future Work

We plan to explore dynamic beta adjustments during the training process to further enhance the model's performance. We hypothesize that dynamically adjusting and rejusting of \( \beta_t \) could guide the model toward better optimization. This approach has shown promising early results but will require further experimentation and refinement.

## References

1. Sohl-Dickstein, J., Weiss, E., Maheswaranathan, N., & Ganguli, S. (2015). Deep Unsupervised Learning using Nonequilibrium Thermodynamics. *Proceedings of the 32nd International Conference on Machine Learning*. https://proceedings.mlr.press/v37/sohl-dickstein15.pdf
3. Ho, J., Jain, A., & Abbeel, P. (2020). Denoising Diffusion Probabilistic Models. *arXiv preprint arXiv:2006.11239*. https://arxiv.org/pdf/2006.11239
4. Dhariwal, P., & Nichol, A. (2021). Improved Denoising Diffusion Probabilistic Models. *arXiv preprint arXiv:2102.09672*. https://arxiv.org/pdf/2102.09672
5. Nachmani, E., San Roman, R., & Wolf, L. (2021). Non-Gaussian Denoising Diffusion Models. arXiv preprint arXiv:2106.07582. https://arxiv.org/pdf/2106.07582

