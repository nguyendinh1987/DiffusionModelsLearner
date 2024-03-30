# Why LDM?
-  It applys noise diffusion on latent space instead of pixel space; therefore, it minimizes computing resource while retaining quality and flexibily of diffusion models
-  It accepts different controllable modality such as image, boundingbox, text
# Model structure and key components:
  <img align="center" src="https://media.licdn.com/dms/image/D4E12AQHVfrhaI1K4Bw/article-cover_image-shrink_423_752/0/1683525082825?e=1717027200&v=beta&t=2T-KlB8QcucSNRu-nsQoECDuwfHZazARql8hvPOXlgk" alt="Sublime's custom image"/>
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
