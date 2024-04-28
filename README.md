<!-- <p align="center">
 <img src="./assets/lumina-logo.png" width="40%"/> 
 <br>
</p> -->

# $\textbf{Lumina-T2X}$: Transform Text into Any Modality, Resolution, and Duration via Flow-based Large Diffusion Transformers

[![GitHub repo contributors](https://img.shields.io/github/contributors-anon/Alpha-VLLM/Lumina-T2X?style=flat&label=Contributors)](https://github.com/Alpha-VLLM/Lumina-T2X/graphs/contributors) 
[![GitHub Commit](https://img.shields.io/github/commit-activity/m/Alpha-VLLM/Lumina-T2X?label=Commit)](https://github.com/Alpha-VLLM/Lumina-T2X/commits/main/)
[![Pr](https://img.shields.io/github/issues-pr-closed-raw/Alpha-VLLM/Lumina-T2X.svg?label=Merged+PRs&color=green)](https://github.com/Alpha-VLLM/Lumina-T2X/pulls)
[![GitHub repo stars](https://img.shields.io/github/stars/Alpha-VLLM/Lumina-T2X?style=flat&logo=github&logoColor=whitesmoke&label=Stars)](https://github.com/Alpha-VLLM/Lumina-T2X/stargazers)&#160;
[![GitHub repo watchers](https://img.shields.io/github/watchers/Alpha-VLLM/Lumina-T2X?style=flat&logo=github&logoColor=whitesmoke&label=Watchers)](https://github.com/Alpha-VLLM/Lumina-T2X/watchers)&#160;
[![GitHub repo size](https://img.shields.io/github/repo-size/Alpha-VLLM/Lumina-T2X?style=flat&logo=github&logoColor=whitesmoke&label=Repo%20Size)](https://github.com/Alpha-VLLM/Lumina-T2X/archive/refs/heads/main.zip)
<!-- [![GitHub issues](https://img.shields.io/github/issues/Alpha-VLLM/Lumina-T2X?color=critical&label=Issues)](https://github.com/PKU-YuanGroup/Video-LLaVA/issues?q=is%3Aopen+is%3Aissue) -->
<!-- [![GitHub closed issues](https://img.shields.io/github/issues-closed/Alpha-VLLM/Lumina-T2X?color=success&label=Issues)](https://github.com/PKU-YuanGroup/Video-LLaVA/issues?q=is%3Aissue+is%3Aclosed) <br> -->
<!-- [![GitHub repo forks](https://img.shields.io/github/forks/Alpha-VLLM/Lumina-T2X?style=flat&logo=github&logoColor=whitesmoke&label=Forks)](https://github.com/Alpha-VLLM/Lumina-T2X/network)&#160; -->

![intro_large](https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/9f52eabb-07dc-4881-8257-6d8a5f2a0a5a)

<!-- [[中文版本]](./README_cn.md) -->

## 📰 News

- **[2024-04-25]** 🔥🔥🔥 **Support 720P video generation with arbitrary aspect ratio. [Demo](#text-to-video-generation)** 🚀🚀🚀
- [2024-04-19] 🔥🔥🔥 Demo released.
- [2024-04-05] 😆😆😆 Code released for Lumina-T2I.
- [2024-04-01] 🚀🚀🚀 We release the initial version of Lumina-T2I for text-to-image generation.

## 🚀 Quick Start

For training and inference, please refer to [Lumina-T2I README.md](./lumina_t2i/README.md#Installation)

## 📑 Open-source Plan

- [x] Lumina-T2I (Training, Inference)
- [ ] Lumina-T2V
- [x] Web Demo
- [x] Cli Demo

## 📜 Index of Content

- [Lumina-T2X](#lumina-t2x)
  - [📰 News](#-news)
  - [🚀 Quick Start](#-quick-start)
  - [📑 Open-source Plan](#-open-source-plan)
  - [📜 Index of Content](#-index-of-content)
  - [Introduction](#introduction)
  - [📽️ Demos](#️-demos)
    - [Text-to-Image Generation](#text-to-image-generation)
    - [Text-to-Video Generation](#text-to-video-generation)
    - [Text-to-3D Generation](#text-to-3d-generation)
    - [More demos](#more-demos)
  - [⚙️ Diverse Configurations](#️-diverse-configurations)

## Introduction

We introduce the $\textbf{Lumina-T2X}$ family, a series of text-conditioned Diffusion Transformers (DiT) capable of transforming textual descriptions into vivid images, dynamic videos, detailed multi-view 3D images, and synthesized speech. At the core of Lumina-T2X lies the **Flow-based Large Diffusion Transformer (Flag-DiT)**—a robust engine that supports up to **7 billion parameters** and extends sequence lengths to **128,000** tokens. Drawing inspiration from Sora, Lumina-T2X integrates images, videos, multi-views of 3D objects, and speech spectrograms within a spatial-temporal latent token space, and can generate outputs at **any resolution, aspect ratio, and duration**.

🌟 **Features**:
- **Flow-based Large Diffusion Transformer (Flag-DiT)**: Lumina-T2X is trained with the **flow matching objective** and is equipped with many techniques, such as RoPE, RMSNorm, and KQ-norm, **demonstrating faster training convergence, stable training dynamics, and a simplified pipeline**.
- **Any Modalities, Resolution, and Duration within one framework**: 
  1. $\textbf{Lumina-T2X}$ can **encode any modality, including mages, videos, multi-views of 3D objects, and spectrograms into a unified 1-D token sequence at any resolution, aspect ratio, and temporal duration.**
  2. By introducing the `nextline` and `nextframe` tokens, our model can **support resolution extrapolation**, i.e., generating images/videos with out-of-domain resolutions **not encountered during training**.
- **Low Training Resources**: Despite increasing token length, which generally extends training time, our Large-DiT reduces the total number of training iterations needed, thus **minimizing overall training time** and computational resources. Moreover, by employing meticulously curated text-image and text-video pairs featuring high aesthetic quality frames and detailed captions, our $\textbf{Lumina-T2X}$ model is learned to generate high-resolution images and coherent videos with minimal computational demands. Remarkably, the default Lumina-T2I configuration, equipped with a 5B Flag-DiT and a 7B LLaMA as the text encoder, **requires only 20% of the computational resources needed by Pixelart-**$\alpha$.

![framework](https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/60d2f248-67b1-43ef-a530-c75530cf26c5)

## 📽️ Demos

### Text-to-Image Generation

<p align="center">
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/27bd36a8-8411-47dd-a3a7-3607c1d5d644" width="90%"/> 
 <br>
</p>

### Text-to-Video Generation

**720P Videos:**

**Prompt:** The majestic beauty of a waterfall cascading down a cliff into a serene lake.

https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/17187de8-7a07-49a8-92f9-fdb8e2f5e64c

https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/0a20bb39-f6f7-430f-aaa0-7193a71b256a

**Prompt:** A stylish woman walks down a Tokyo street filled with warm glowing neon and animated city signage. She wears a black leather jacket, a long red dress, and black boots, and carries a black purse. She wears sunglasses and red lipstick. She walks confidently and casually. The street is damp and reflective, creating a mirror effect of the colorful lights. Many pedestrians walk about.

https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/7bf9ce7e-f454-4430-babe-b14264e0f194


**360P Videos:**

https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/d7fec32c-3655-4fd1-aa14-c0cb3ace3845

### Text-to-3D Generation

https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/cd061b8d-c47b-4c0c-b775-2cbaf8014be9

### More demos

For more demos visit [this website](https://lumina-t2-x-web.vercel.app)
<!-- ### High-res. Image Editing

<p align="center">
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/55981976-c989-4f07-982a-1e567c7078ef" width="90%"/> 
 <br>
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/a1ac7190-c49c-4d8b-965c-9ccf83a4f6a7" width="90%"/> 
</p>

### Compositional Generation

<p align="center">
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/8c8eb921-134c-4f55-918a-0ad07f9a47f4" width="90%"/> 
 <br>
</p>

### Resolution Extrapolation

<p align="center">
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/e37e2db7-3ead-451e-ba18-b375eb773578" width="90%"/> 
 <br>
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/9da47c34-5e09-48d3-9c48-78663fd01cc8" width="100%"/> 
</p>

### Consistent-Style Generation

<p align="center">
 <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/6403417a-42c6-4048-9419-375d211e14bb" width="90%"/> 
 <br>
</p> -->

## ⚙️ Diverse Configurations

We support diverse configurations, including text encoders, DiTs of different parameter sizes, inference methods, and VAE encoders. Additionally, we offer features such as 1D-RoPE, image enhancement, and more.

<p align="center">
  <img src="https://github.com/Alpha-VLLM/Lumina-T2X/assets/54879512/221de325-d9fb-4b7e-a97c-4b24cd2df0fc" width="100%"/>
 <br>
</p>


<!--

## 📄 Citation

```
@inproceedings{luminat2x,
  author    = {},
  title     = {},
  booktitle = {},
  pages     = {}
  year      = {2024}
}
```

## Star History

 [![Star History Chart](https://api.star-history.com/svg?repos=Alpha-VLLM/Lumina-T2X&type=Date)](https://star-history.com/#Alpha-VLLM/Lumina-T2X&Date) -->
