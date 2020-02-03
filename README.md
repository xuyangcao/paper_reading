- [Review](#review)
  - [2019](#2019)
    - [Machine Learning Techniques for Biomedical Image Segmentation: An Overview of Technical Aspects and Introduction to State-of-Art Applications](#machine-learning-techniques-for-biomedical-image-segmentation-an-overview-of-technical-aspects-and-introduction-to-state-of-art-applications)
- [Segmentation](#segmentation)
- [Detection](#detection)

# Review 
## 2019
### Machine Learning Techniques for Biomedical Image Segmentation: An Overview of Technical Aspects and Introduction to State-of-Art Applications

**Comparision between Traditional Methods and Deep Learning based Methods** 
| Methods | Advantage | Disadvantage |
| ------- | --------- | ------------ |
| Gredient based methods | Fast | Prone to image noise and artifacts that result in missing or diffuse organ boundaries. |
| Graph based methods (MRF et al.) | | High computational cost due to iterative schedume. |
| Superivsed methods + prior knowledge | capture shape well and generate more accurate results than unsupervised methods | Limitated results when dealing with fuzzy boundaries |
| Deep learning methods | Automatic feature extration scheme instead of manual feature extraction, More accurate | Large computational cost, and large amount of data |

**Deep Learning based Methods**
| Methods | Advantage | Disadvantage |
| ------- | --------- | ------------ |
| Patch based CNN | Alleviate the coputational burden | 1. loss of spatial infortation<br> 2. too small patchs means less information could be extracted<br> 3. may increase training time due to the duplicated computation of pixels |

| Challenges | Current Solutions | 
| ---------- | ----------------- |
| Limited Training Data | 1. Data Augmentation<br> 2. Transfer Learning<br> 2. Generate data using GAN
| Volumetric 3D Data cost training time and computer memory | 1. use 2D segmentation architectures instead of 3D architectures<br> 2. *use 2.5D architectures* (an input data as several slice images, orthogonal images, maximum or minimum intensity projection) |
| Requires a lot of Hyperprameter Tuning | None |












# Segmentation

# Detection