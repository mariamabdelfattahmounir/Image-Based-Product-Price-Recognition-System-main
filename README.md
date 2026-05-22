 Image-Based-Product-Price-Recognition-System
=================================================

<img src="https://github.com/Salma-Salah420/Image-Based-Product-Price-Recognition-System/blob/4029ec771f66e8f3df6c37861d8ebc684d6ee519/images/OIP.webp" width="600"/>

Problem Definition:
========================
Given a product name as a query, we need to retrieve the top‑K most similar products from a product catalog.
Similarity is measured in the embedding space using cosine similarity.
========

Challenges:-
==============

Product names may be short, ambiguous, or contain typos.

Different products may have similar names but different meanings (e.g., "iPhone 13" vs "iPhone 13 case").

Need to choose an embedding model that captures semantic not just lexical similarity.

Product Detection: Identify products in images using computer vision algorithms.

Price Recognition: Detect and read price tags from product images.

Multiple Products Handling: Works with images containing several products at once.

Data Export: Save extracted product names and prices in structured formats like CSV or JSON.

Cross-Platform: Works with images captured by mobile phones, cameras, or online sources.

## ResNet50 Feature Extraction Experiments

During the feature extraction stage, two different configurations of the ResNet50 backbone were evaluated to analyze the quality and discriminative power of the generated image embeddings.

### 1. Frozen ResNet50 Backbone
In this configuration, the pretrained ResNet50 weights were kept frozen, meaning that no gradient updates were applied to the convolutional backbone during training. The model was therefore used purely as a fixed feature extractor.

### 2. Fine-Tuned ResNet50 Backbone
In the second configuration, the ResNet50 layers were unfrozen and allowed to update during training, enabling the network to adapt its learned representations to the target dataset.

---

## Experimental Results

| Experiment | Number of Images | Feature Dimension | Intra-class Similarity | Inter-class Similarity | Separation Score |
|---|---:|---:|---:|---:|---:|
| `img224_bs32_frozen` | 3693 | 2048 | 0.5576 | 0.4727 | **0.0848** |
| `img256_bs32_finetune` | 3693 | 2048 | 0.5687 | 0.4870 | 0.0817 |

---

## Analysis

The frozen ResNet50 configuration achieved the highest separation score (**0.0848**), indicating better discrimination between different classes in the feature space.

Although the fine-tuned configuration slightly improved intra-class similarity, it also increased inter-class similarity, which reduced the overall feature separability.

These results suggest that using ResNet50 as a frozen pretrained feature extractor produced more robust and generalizable visual representations for this task.

---

## Final Decision

Based on the experimental evaluation, the frozen ResNet50 backbone was selected for the final multimodal pipeline because it generated more discriminative image features and achieved the best overall class separation performance.
_____________________________________________________________________________________________________
Model 1: Sentence Transformer:
=============================







Team members&&their roles:
=========================
Salma Salah >>> Bert 

Mariam Abdel Fattah>>> DistillBert 

Marina Shnouda >>>  Effientnet 

Kareem Hamada >>> Resnet 

Shahd Mohamed>> Fusion Model&&Concatenate Results
