- [Review](#review)
  - [2019](#2019)
    - [Machine Learning Techniques for Biomedical Image Segmentation: An Overview of Technical Aspects and Introduction to State-of-Art Applications](#machine-learning-techniques-for-biomedical-image-segmentation-an-overview-of-technical-aspects-and-introduction-to-state-of-art-applications)
    - [Understanding Deep Learning Techniques for Image Segmentation](#understanding-deep-learning-techniques-for-image-segmentation)
    - [Deep Semantic Segmentation of Natural and Medical Images: A Review](#deep-semantic-segmentation-of-natural-and-medical-images-a-review)
- [Segmentation](#segmentation)
  - [Data Augmentation](#data-augmentation)
    - [K. Abhishek and G. Hamarneh. Mask2Lesion: Mask-Constrained Adversarial Skin Lesion Image Synthesis[C]. Simulation and Synthesis in Medical Imaging, Cham, 2019:71–80.](#k-abhishek-and-g-hamarneh-mask2lesion-mask-constrained-adversarial-skin-lesion-image-synthesisc-simulation-and-synthesis-in-medical-imaging-cham-201971%e2%80%9380)
  - [Transfer learning](#transfer-learning)
    - [Maithra Raghu, Chiyuan Zhang, Jon M. Kleinberg, Samy Bengio. Transfusion: Understanding Transfer Learning for Medical Imaging. NeurIPS 2019: 3342-3352](#maithra-raghu-chiyuan-zhang-jon-m-kleinberg-samy-bengio-transfusion-understanding-transfer-learning-for-medical-imaging-neurips-2019-3342-3352)

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



### Understanding Deep Learning Techniques for Image Segmentation

**Defination:**

- Image segmentation can be defined as a specific image processing technique which is used to divide an image into two or more meaningful regions.
- Image segmentation can also be seen as a process of defining boundaries between separate semantic entities in an image.
-  From a more technical perspective, image
segmentation is a process of assigning a label to each pixel in the image such that pixels with the same label are connected with respect to some **visual** or **semantic** property

**Categories**

| Categories | Task | Notes |
| ---------- | ---- | ----- |
| Semantic Segmentation | Each pixel is classified into one of the predefined set of classes such that pixels belonging to the same class belongs to an unique semantic entity in the image. | The semantics depends on the **data** and the **problem** that needs to be addressed |
| Saliency Detection | focusing on the most important object in a scene|

**Application**

![](images/Application.png)

**Comparization**

|   | Traditional Methods | Deep Learning Based Methods |
| - | ------------------- | --------------------------- |
| **Advantage** |  | 1. automated feature learning |
| **Disadvantage** | 1. the results dependent on the quality of feature extracted by the domain experts<br> 2. humans are bound to miss latent or abstract features for image segmentation |

### Deep Semantic Segmentation of Natural and Medical Images: A Review

**Categories:**
![](./images/03_Categories.png)

**Potentional Difficulty**

| difficulty | solutions | pros | cons |
| ---------- | --------- | ---- | ---- |
| medical image can be in high dimentions (2D and 3D) | processed as sub-volumes (images) | reduce computing cost | prevent models capturing spatial information / relationships properly |
| lack of annotated data | 1. semi- or un-supervised learning<br> 2. encoding prior knowledge into model | 


**Potential Future Directions**

- Going beyond pixel intensity-based scene understanding via incorporating prior knowledge.
- Creating large 2D and 3D publicly available medical benchmark datasets for semantic image segmentation such as the Medical Segmentation Decathlon.
- Exploring reinforcement learning approaches for semantic (medical) image segmentation to mimic the way human does delineation





# Segmentation
## Data Augmentation

### K. Abhishek and G. Hamarneh. Mask2Lesion: Mask-Constrained Adversarial Skin Lesion Image Synthesis[C]. Simulation and Synthesis in Medical Imaging, Cham, 2019:71–80.

**Contribution**
- propose a GAN-based augmentation of the original dataset in order to improve the segmentation performance
- use the segmentation masks available in the training dataset to
train the Mask2Lesion model, and use the model to generate new lesion images given any arbitrary mask, which are then used to augment the original training dataset

![](./images/mask2lesion_architecture.png)
![](./images/mask2lesion_results.png)

**Pros**

The trained mask2lesion model can generate original images using only arbitrary binary mask, thus can be easily applied to other dataset.

**Cons**

don't know


## Transfer learning

### Maithra Raghu, Chiyuan Zhang, Jon M. Kleinberg, Samy Bengio. Transfusion: Understanding Transfer Learning for Medical Imaging. NeurIPS 2019: 3342-3352


**Problem**
- transfer learning is typically performed by taking a standard ImageNet architecture along with its pretrained weights, and then fine-tuning on the target task
- However, ImageNet classifcation and medical image diagnosis have considerable diferences.
-  There is thus an open question of how much ImageNet feature reuse is helpful for medical images?

**Difference between natural image classcification and medical image analysis**

|   | ImageNet dataset | Medical image dataset |
| - | ---------------- | --------------------- |
| **Classes** | 1000 | less than 10 in most tasks | 
| **image size**  | smaller | larger than natural image |
| **Dataset size**| a million | several thousands or a couple of hundred |
| **data property**| there is often a clear global subject of the image | variations in local textures to identify pathologies | 

**Contribution**
-  evaluate the performance of standard architectures for natural images such as ImageNet, as well as a family of non-standard but smaller and simpler models, on two large scale medical imaging tasks, for which transfer learning is currently the norm
-  We show there are also feature-independent benefits to pretraining — reusing only the scaling of the pre-trained weights but not the features can itself **lead to large gains in convergence speed**.


**Results**

![](./images/transfusion_filter.png)
![](./images/transfusion_converge.png)

- in all of these cases, transfer does not signifcantly help performance
- smaller, simpler convolutional architectures perform comparably to standard ImageNet models
- ImageNet performance is not predictive of medical performance.