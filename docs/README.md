# Why LDM?
-  It applys noise diffusion on latent space instead of pixel space; therefore, it minimizes computing resource while retaining quality and flexibily of diffusion models
-  It accepts different controllable modality such as image, boundingbox, text
# Model structure and key components:
- ![image](https://www.researchgate.net/publication/364442071/figure/fig3/AS:11431281091064587@1666286349233/The-architecture-of-the-latent-diffusion-model-LDM-that-is-considered-a-revolutionary.ppm)
- Image conpression and depression: KL-regularized autoencoder was used as a **first_state_model** to encode images into latent features and decode latent features into image. This autoencoder can be trained separatedly on different datasets, such as ImageNet, FFHQ, celebA-HQ, ADE20K, COCO-stuff, FaceHQ, and so on [2].
- Latent space diffusion is an Unet model:
- Condition embeding:
  - Concat
  - Attention
  - CrossAttention
- Speedup
# References
1. [High resolution image synthesis with latent diffusion models](https://arxiv.org/pdf/2112.10752.pdf)
2. [Taming-transformer](https://github.com/CompVis/taming-transformers)
