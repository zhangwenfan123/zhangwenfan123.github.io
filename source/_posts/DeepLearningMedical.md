---
title: A descriptive framework for the field of deep learning applications in medical images
date: 2022-06-09
tags: Deep_Learning
category: Artificial Intelligence
excerpt: Deep learning in medical image analysis is a typical interdisciplinary application, which needs support and cooperation of computer techniques and medical experience, and has broad application prospects.
author: Zhang Wenfan
authorURL: 
url: 
copyrightText: 
---

$\underline{\text{-01. Questions}}$

>1. How to define the "descriptive framework"? The work of this paper shows comprehensive analysis of historical papers, but this work is still a little confusing to me, why it could be called framework?

>2. It is noticed that GAN is also used in the medical images analsis. Actually, in the medical industry, personal health senario is quite complex. Is it meaningful trying to train generative data by algorithm before we really understand the actual medical situation?

$\underline{\text{00. Themes and Topics}}$

- 0.1 **Deep Learning**
    - **Supervised Learning**
    - **Weakly Supervised Learning**
    - **Unsupervised learning**

*Supervised Learning*

>Supervised learning represents a learning method that uses data with manual annotation labels to train the network. For classification,image-level or patch-level labels are required. 

>. In the supervised setting, given datasets D = {(x1, y1), (x2, y2), . . . , (xN , yN )}, the corresponding loss aims to minimize the distance between the predicted value y′ and the ground truth y, as Eq. (1).

$$
\mathscr{L}_{supervised} = \mathop{min}\limits_{\theta} \frac{1} {N} \sum_{i=1}^N(y_i',y_i)
$$

*Weakly Supervised Learning*

>Weakly supervised learning mainly consists of incomplete supervision, inexact supervision and inaccurate supervision [104], where incomplete supervision is more common in the medical field.

>The datasets in incomplete supervision can be denoted as D = {(x1, y1), (x2, y2), . . . , (xl, yl), xl+1, . . . , xN }, where only a small subset of labeled data is available. 

*Unsupervised learning*

>Unsupervised learning attempts to train a model with unlabeled data. The Generative unsupervised model is represented by Autoencoder (AE), Sparse Autoencoder (SAE) and Generative Adversarial Network (GAN), which focuses on pixel-level reconstruction error. However, pixel-level generation is computationally expensive. Recently,self-supervised learning (SSL) has become more and more popular.

>Contrastive learning (CL) is a type of SSL, which has achieved great progress in computer vision, natural language processing and other fields. It hopes to distinguish different inputs in the feature space. The loss function is shown in formula (2) [108], aiming to measure the similarity between two features.

$$
\mathscr{L} = \mathbb{E}_{x,x^+,x^-}[-log\frac{e^{f(x)^T}f(x^+)} {e^{f(x)^T f(x^+)}+e^{f(x)^T f(x^-)}}]
$$

- 0.2 **Convolutional neural network**
    - **Classification architectures**
    - **Object detection architectures**
    - **Segmentation architectures**

>At present, the Convolutional Neural Network (CNN) is the most popular deep neural network for computer vision. The original deep network architecture used for image classification, object detection and segmentation was born based on CNN in supervised learning scenarios.

>Almost all representative articles are based on CNN. The convolution layer consists of several convolution kernels (filters) $(g^1,g^2,\cdots,g^k)$ and each can be expressed as a linear function in Eq.

$$
g^k(x,y) = 
\sum_{u=-m}^m \sum_{v=-n}^n \sum_{w=-d}^w W_k(u,v,w)I(x-u,y-v,z-w)
$$

*Classification Architecture*

>For the classification task, there is only one object of a single category in an image/patch. The main process of classification is to feed images into a deep learning model, where the image-level/patch-level labels are required, and finally output the category or its corresponding probability of this image.

*Object detection architectures*

>Medical image detection is an object detection task in deep learning, where there are multiple objects and categories in one image. Besides classifying images, the typic feature of object detection is locating the position or coordinates of an object with a bounding box. 

*Segmentation architectures*

>Deep learning-based segmentation can be divided into ordinary segmentation, semantic segmentation, and instance segmentation. In the medical field, semantic segmentation is the most common. Compared with image classification and object detection, segmentation is more accurate and more complicated. It outputs pixel-level labels instead of image-level labels. Besides the bounding box, it can also output the exact boundary of the object (Fig. 7).

- 0.3 **Recurrent neural network**

>Recurrent Neural Network (RNN) is a neural network designed to process sequence data.

$$
h_t^i = f(U^{(i)}h_t^{(i-t)}+W^{(i)}h_{(t-1)}^i+b^{(i)})
$$

>Finally, the output layer is only activated based on the hidden
state of the last layer, that is, the lth layer, which can be shown
in Eq. (7).

$$
Q_t = f(W^{(out)}h_t^l+b^{(out)})
$$


- 0.4 **Generative adversarial network**

>Generative Adversarial Network (GAN) introduced by Good fellow et al. [119] is one of the most common architectures in unsupervised learning. It consists of a generator (G) and a discriminator (D). The two of them are playing against each other. The G is used to capture the distribution of the input samples and generate fake images from noise prior as close as possible to the real images, so as to deceive the D. In contrast, the D needs to distinguish whether the sample comes from real data or generated data as much as possible. The value function V(D, G) is shown in Eq. (6).

$$
V(G,D) = 
\mathop{min}\limits_{G}\enspace\mathop{max}\limits_{D} \mathbb{E}_{x\sim p_data}(x)[logD(x)]+\mathbb{E}_{z\sim p_z}(z)[log(1-D(G(z)))]
$$


$\underline{\text{01. Applications in medical images}}$

- 0.1 **Applications of classification**
    - **Pathologic image**
    - **X-ray**
    - **OCT and fundus image**
    - **Endoscopic image**
    - **Dermoscopic image**
    - **EEG / ECG**
    - **Other images**

>This section summarizes the application of 77 representative articles for the field of deep learning in medical image classification,detection, segmentation and generation.

*Pathologic image*

>For cancer, pathological diagnosis is a gold standard in clinical practice. The conventional diagnostic way is to visually inspect histopathology images by experienced pathologists.

*X-ray*

>Mammography is one of the most important modes in X-ray images and the main diagnostic tool for breast cancer. 

*OCT and fundus image*

>Almost all articles that we surveyed on OCT and fundus images were about classification. OCT and fundus images are diagnostic tools specifically used to examine retinal abnormalities. Diabetic retinopathy (DR), glaucomatous optic neuropathy (GON) and agerelated macular degeneration (AMD) are common retinal diseases.

*Endoscopic image*

>Endoscopy produces video and it always takes a long time
to analyze, even for professional endoscopists. There have been
Narrow band imaging (NBI) — based deep learning studies about
distinguishing normal and abnormal colorectal polyps [44,45].
NBI is one of the most important forms of endoscopy, with three
modes of far focus, near focus and normal focus. 

*Dermoscopic image*

>Dermoscopic image-based deep learning models are often
used to diagnose melanoma. There are two related studies from
Heidelberg University in Germany. 

*EEG / ECG*

>EEG and ECG are biological signals and usually seen in clinical
diagnosis with special image modalities.

- 0.2 **Applications of detection**
    - **Endoscopic image**
    - **X-ray and CT**
    - **Other images**

*Endoscopic image*

>Detection is more challenging in endoscopy than in other
ordinary images. For colonoscopy, it consists of thousands of
frames, probably 20–35 frames per second. The polyp can be
detected in only a few frames [68]. Therefore, real-time detection
in endoscopy is of great significance.

*X-ray and CT*

>Both chest radiograph and CT are widely used in clinical diagnosis. Chest radiograph requires less dose but has poorer image quality. In contrast, CT has a wider range of applications
and higher image quality. However, even low dose CT scans
require 50–100 times radiation dose than single-view chest radiograph [74]


- 03 **Applications of segmentation**
    - **MRI**
    - **CT**
    - **Other images**

*MRI*

>MRI has a superior high-resolution soft-tissue contrast and
can display lesions from multiple views (horizontal, coronal, and
sagittal, for example). Therefore, it has been most widely used in
the diagnosis of pelvic, heart, brain, knee joints and other parts.

*CT*

>Roy et al. [81] developed a framework based on few-short
learning and ‘squeeze & excite’ blocks to realize CT volumetric
image segmentation. Chen et al. [94] achieved a bidirectional
cross-modality adaptation between MRI and CT images via image
and feature alignment. 


- 04 **pplications for image generation**

>This section is highly relevant to PET, CT and MR, and GAN is
widely welcomed here. In fact, considerable articles also belong
to the segmentation task. Here we set them as a separate image
generation section, including image generation in a narrow sense,
image translation, image denoising, image reconstruction, image
attenuation correction, and so on.


$\underline{\text{02. Discussion and Conclusion}}$
   
>The analysis of medical images is an important tool for clinical
diagnosis. In this survey, 2068 articles published on PubMed
on and before June 26, 2020 about deep learning in medical
images were reviewed. The number of articles has experienced
exponential growth since 2017.

>The main contribution in this survey is providing a descriptive
framework for reviewing and using LDA as a quick analysis tool
for literature review.

