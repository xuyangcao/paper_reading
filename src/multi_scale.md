- [Multiscale Semantic Segmentation](#multiscale-semantic-segmentation)
  - [DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs, PAMI, 2018](#deeplab-semantic-image-segmentation-with-deep-convolutional-nets-atrous-convolution-and-fully-connected-crfs-pami-2018)
  - [Rethinking Atrous Convolution for Semantic Image Segmentation, Arxiv, 2017](#rethinking-atrous-convolution-for-semantic-image-segmentation-arxiv-2017)

## Multiscale Semantic Segmentation

### DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs, PAMI, 2018

**Challenges and Solution**
| Challenge | Solution |
| --------- | -------- |
|The first challenge is caused by the repeated combination of max-pooling and downsampling (‘striding’) performed at consecutive layers of DCNNs originally designed for image classification. | we remove the downsampling operator from the last few max-pooling layers of DCNNs and instead upsample the filters in subsequent convolutional layers, resulting in feature maps computed at a higher sampling rate |
| The second challenge is caused by the existence of objects at multiple scales. | Instead, motivated by spatial pyramid pooling [19], [20], we propose a computationally efficient scheme of resampling a given feature layer at multiple rates prior to convolution |
| The third challenge relates to the fact that an object-centric classifier requires invariance to spatial transformations, inherently limiting the spatial accuracy of a DCNN. | we boost our model’s ability to capture fine details by employing a fully-connected Conditional Random Field (CRF) |


**Useful Information**
- Compared to regular convolution with larger filters, atrous convolution allows us to effectively enlarge the field of view of filters without increasing the number of parameters or the amount of computation.

**Method**

![](../images/multi_scale/deep_lab_architecture.png)

![](../images/multi_scale/deep_lab_atrous_convolution_1d.png)

![](../images/multi_scale/deep_lab_atrous_convolueion_2d.png)

![](../images/multi_scale/deep_lab_aspp_network.png)

**Result and Conclusion**

![](../images/multi_scale/deep_lab_result_1.png)

- Our experimental results show that the proposed method significantly advances the state-of-art in several challenging datasets, including PASCAL VOC 2012 semantic image segmentation benchmark, PASCAL-Context, PASCAL-Person-Part, and Cityscapes datasets


### Rethinking Atrous Convolution for Semantic Image Segmentation, Arxiv, 2017

**Challenges and Problems**
- The first one is the **reduced feature resolution** caused by consecutive pooling operations or convolution striding, which allows DCNNs to learn increasingly abstract feature representations. However, this invariance to local image transformation may impede dense prediction tasks, **where detailed spatial information is desired**. 
- Another difficult comes from the existence of **objects at multiple scales.**

**Different Models on Multiscale Object Segmentation**

| Architecture | pros | cons |
| ------------ | ----- | ---- |
| Image Pyramid | can extract features for each scale input | 1. The main drawback of this type of models is that it does not scale well for larger/deeper DCNNs due to limited GPU memory and thus it is usually applied during the inference stage<br> 2. This method works but comes at the cost of computing feature responses at all DCNN layers for multiple scaled versions of the input image |
| Encorder-Decorder Structure | 1. the encoder where the spatial dimension of feature maps is gradually reduced and thus longer range information is more easily captured in the deeper encoder output<br> 2. the decoder where object details and spatial dimension are gradually recovered | More couputational memory |
| Context Module | contains extra modules laid out in cascade to encode long-range context, for example Dense CRF |  |
| Spatial pyramid pooling | capture context at several ranges |  |

![](../images/multi_scale/deeplab_v3_different_architectures_to_capture_multi_scale_context.png)

**Contribution**
- In this work, we mainly explore atrous convolution as a **context module** and tool for **spatial pyramid pooling.**
- To further capture global context, we propose to augment ASPP with
image-level features, similar to [58, 95].

![](../images/multi_scale/deeplab_v3_architecture_0.png)

![](../images/multi_scale/deeplab_v3_architecture_1.png)


**Result and Conclusion**

- Going deeper with atrous convolution
  ![](../images/multi_scale/deeplab_v3_result_1.png)
  This results illustrate that consecutive striding is harmful for semantic segmentation.

  ![](../images/multi_scale/deeplab_v3_result_2.png)
  This results show that the performance improves as more blocks are added, but the margin of improvement becomes smaller.

- Atrous Spatial Pyramid Pooling
  ![](../images/multi_scale/deeplab_v3_result_3.png)