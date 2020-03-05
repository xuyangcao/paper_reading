- [Data Augmentation](#data-augmentation)
  - [K. Abhishek and G. Hamarneh. Mask2Lesion: Mask-Constrained Adversarial Skin Lesion Image Synthesis[C]. Simulation and Synthesis in Medical Imaging, Cham, 2019:71–80.](#k-abhishek-and-g-hamarneh-mask2lesion-mask-constrained-adversarial-skin-lesion-image-synthesisc-simulation-and-synthesis-in-medical-imaging-cham-201971%e2%80%9380)

## Data Augmentation

### K. Abhishek and G. Hamarneh. Mask2Lesion: Mask-Constrained Adversarial Skin Lesion Image Synthesis[C]. Simulation and Synthesis in Medical Imaging, Cham, 2019:71–80.

**Contribution**
- propose a GAN-based augmentation of the original dataset in order to improve the segmentation performance
- use the segmentation masks available in the training dataset to
train the Mask2Lesion model, and use the model to generate new lesion images given any arbitrary mask, which are then used to augment the original training dataset

![](../images/augmentation/mask2lesion_architecture.png)
![](../images/augmentation/mask2lesion_results.png)

**Pros**

The trained mask2lesion model can generate original images using only arbitrary binary mask, thus can be easily applied to other dataset.

**Cons**

don't know