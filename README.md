# **Diabetic Retinopathy Detection Using CNN with Residual Block and DCGAN**



---

## **Table of Contents**
1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Preprocessing](#preprocessing)
4. [Data Augmentation](#data-augmentation)
5. [Model Architecture](#model-architecture)
6. [Results](#results)

---

## **Introduction**

Diabetic Retinopathy (DR) is a microvascular complication that occurs as a result of diabetes and is recognized as one of the leading causes of blindness worldwide. The disease primarily affects the blood vessels in the retina, leading to a range of vision problems. As DR progresses, it manifests as a spectrum of stages, starting from no DR, which indicates the absence of visible abnormalities, to mild, moderate, and severe stages, and finally to proliferative DR, the most advanced form where new, abnormal blood vessels start to grow in the retina. 
These different stages of DR are associated with various retinal abnormalities, such as microaneurysms, hemorrhages, exudates, and neovascularization, which require careful and precise examination. Accurate and automated detection of DR severity can significantly improve the efficiency and effectiveness of large-scale screening programs, particularly in resource-constrained environments where access to trained ophthalmologists and diagnostic equipment is limited. 
In this work, we focus on the classification of retinal images into five distinct categories, ranging from No DR to Proliferative DR. Unlike traditional feature extraction methods, which rely heavily on manual input and domain expertise, end-to-end deep learning approaches like Convolutional Neural Networks (CNNs) directly learn discriminative features from data. CNN-based architectures are particularly well-suited for this problem due to their ability to capture spatial hierarchies in images. 

---

## **Dataset**

- **Source**: [Diabetic Retinopathy 2015 Data Colored Resized]([https://www.kaggle.com/datasets/tanlikesmath/diabetic-retinopathy-resized](https://www.kaggle.com/datasets/sovitrath/diabetic-retinopathy-2015-data-colored-resized))
- **Structure**:
  ```bash
  dataset/
  ├── No DR/
  ├── Mild/
  └── Moderate/
  ├── Severe/
  └── Proliferate/
  ```

---

## **Preprocessing**

Medical images can be challenging to analyze due to their complexity and variations. To address these challenges, several preprocessing techniques are applied in the proposed model to enhance image quality and ensure dataset consistency for better classification results.

The following preprocessing techniques are employed:

1. **Circle-Crop**: Removes unnecessary background noise and standardizes images to a uniform size.
2. **Median Subtraction**: Reduces noise without affecting edges by applying a median filter, providing a faster alternative to other filters.
3. **Gamma Correction**: Adjusts pixel saturation in non-linear ways, controlling the relationship between pixel values and actual image brightness.
4. **Adaptive Histogram Equalization**: Enhances local details and improves image contrast by considering multiple histograms.

These preprocessing steps are essential for preparing medical images for accurate classification by the model.

---

## **Data Augmentation**

To tackle the class imbalance in the dataset, a combination of conventional and advanced data augmentation techniques was applied:

1. **Conventional Augmentations**: Techniques such as rotation, flipping, shearing, zooming, width shift, height shift, and brightness adjustments were applied to all classes.
2. **GAN-based Augmentation**: Underrepresented classes (all except No DR) were further augmented using Deep Convolutional GANs (DC-GANs). These GAN-generated synthetic images enriched the training set with diverse and realistic retinal fundus images.

The use of DC-GANs, which combine a generator and a discriminator in an adversarial setup, helped the model learn robust representations for rare classes, improving classification performance.

Visual results such as the image classification distribution in the dataset, the sample of real and fake images, and pixel intensity distribution can be found in 'ML_report_final.pdf' file.

---
  
  ## **Model Architecture**

The proposed model is a Convolutional Neural Network (CNN) enhanced with residual blocks, designed for effective classification of retinal fundus images across five DR severity levels. The architecture includes:

1. **Input Layer**: Accepts resized retinal images of dimensions 224x224x1.
2. **Convolutional Layers**: Utilizes zero-padding and max pooling for preserving information and reducing dimensionality, with ReLU activation functions to introduce non-linearity.
3. **Residual Blocks**: Addresses the vanishing gradient problem. Each block contains a convolutional block and two identity blocks, enabling efficient training of deeper networks.
4. **Identity Blocks**: Maintains the dimensionality of the input without shortcut connections, aiding in effective feature extraction.
5. **Fully Connected Layers**: Transforms high-dimensional feature maps into lower-dimensional representations, preparing them for classification.
6. **Output Layer**: Includes a softmax layer to produce probabilities for five classes: No DR, Mild, Moderate, Severe, and Proliferative DR.

Refer to the `ML_report_file.pdf` file for details.

---

## **Results**

| Metric         | Value     |
|----------------|-----------|
| Accuracy       | 0.987%    |

Visual results such as confusion matrices can be found in the `ML_report_file.pdf` file.

---

**Happy Coding!**
