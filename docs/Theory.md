# Why LDM?
-  It applys noise diffusion on latent space instead of pixel space; therefore, it minimizes computing resource while retaining quality and flexibily of diffusion models
-  It accepts different controllable modality such as image, boundingbox, text
# How does it work?
# Model structure and key components:
<div align="center">
  <img src="https://github.com/CompVis/latent-diffusion/raw/main/assets/modelfigure.png" alt="Sublime's custom image"/>
</div>

- <div align="left"> Image autoencoder and decoder: KL-regularized autoencoder was used as a **first_state_model** to encode images into latent features (encoder E) and decode latent features into image (decoder D). This autoencoder can be trained separatedly on several datasets, such as ImageNet, FFHQ, celebA-HQ, ADE20K, COCO-stuff, FaceHQ, and so on to achieve an universal autoencoder model [2].</div>

- Latent space diffusion is an Unet model: It was train to predict noise embeded into the image. [DiffusionModel](https://github.com/nguyendinh1987/LatentDiffusion_Practice/blob/main/docs/DiffusionModel.md)

- Conditional mechanisms: There is an additional model compressing conditional modality into latent features which can be injected into the diffusion Unet model to augment generative process using concatination or attension layers. 
  - Time
  - Text
  - Boundingbox
  - Images (segmentation map, image)

# Other notes:
- Diffusion models belong to the class of likelihood-based models. What is the likehood-based models?

# References
1. [High resolution image synthesis with latent diffusion models](https://arxiv.org/pdf/2112.10752.pdf)
2. [Taming-transformer](https://github.com/CompVis/taming-transformers)
