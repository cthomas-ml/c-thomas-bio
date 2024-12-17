---
title: "Interpreting vision models with sparse dictionary learning: a case for hierarchical learning"
categories:
  - Artificial Intelligence
tags:
  - Alignment
  - Safety
  - Proposal
---


Recently, Anthropic demonstrated [the power of sparse dictionary learning as an interpretability tool](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html) in a large language model. They applied the method to a single embedding layer of a large network to identify a basis of more interpretable features, and [demonstrated control](https://www.anthropic.com/news/golden-gate-claude) of the model output by activating the combination of neurons responsible for single, interpretable features. The work shows that the model is knowledgeable in a meaningful way, but that the meaning is hard to discern in the lower-dimensional neuron basis. By identifying a more interpretable, higher-dimensional basis, Anthropic researchers lay the groundwork to establish whether the model learned desired relationships and tailor fine-tuning and model controls accordingly. 
<!-- Note: not all recovered features appear to be meaningful, which may be due to shortcomings in either the original model or the sparse dictionary learning approach. -->

In this post I consider how one might apply the sparse dictionary learning method to a computer vision or multimodal model.  I hypothesize that it will be less effective at uncovering controllable, interpretable features in common vision models due to a fundamental difference in training data for each modality. I further suggest that a vision model optimized for hierarchical understanding will be a better starting point for sparse dictionary learning interpretability. 

## We train LLMs differently from vision models 

LLMs are trained with concept hierarchies and a sense of logical entailment, where vision models are trained by repetition across large collections of images and their labels. In vision model training, we don't consider relationships of the objects within or between images. 

The largest generative language models demonstrate hierarchical consistency and readily generalize to unseen phrases. 
In contrast, foundational vision models like AlexNet, ImageNet and even SAM are known to 
rely on spurious correlations, 
generalize poorly to unseen data and to lack both intra- and inter-image hierarchical consistency. 

<!-- SAM is one of the most powerful vision models available today, but it lacks intra-image hierarchical consistency. In the figure below, reproduced from Figure 6 of [*Learning Hierarchical Image Segmentation For Recognition and By Recognition*](https://openreview.net/forum?id=IRcv4yFX6z), SAM correctly identifies a fishing scene, but semantically gives the label 'fish' to both the man and fish in the image.  -->

<!-- ![Fig 6 from *Learning Hierarchical Image Segmentation For Recognition and By Recognition*]({{site.baseurl}}/assets/images/CAST-SAM-fishing.png) -->

Using sparse dictionary learning to uncover meaningful features relies on the model containing enough of them. While it’s clear that vision models encode useful information, it may be more difficult to extract and interpret than in sentence encoders that are directly optimized with logical entailment and concept hierarchy. 



## Vision models can be trained with concept hierarchy

We have established that sparse dictionary learning is an excellent tool for interpretability and control of AI models, but that it may not readily apply to common vision models due to fundamental differences in how LLMs and vision models learn and generalize.

Understanding and implementing concept hierarchies and logical entailment in vision models is an active area of research.
In their work, [*Emergent Visual-Semantic Hierarchies in Image-Text Representations*](https://arxiv.org/pdf/2407.08521)  (ECCV 2024), M. Alper and H. Averbuch-Elor studied emergent concept hierarchy in the CLIP model, introduced a metric to quantify it, and fine-tuned the model on this metric to produce the "RE-CLIP" model, with quantitative and qualitative improvement to concept hierarchy and inter-image consistency in the model’s latent representations. 


The CAST model was introduced at ICLR 2024 in [*Learning Hierarchical Image Segmentation For Recognition and By Recognition*](https://openreview.net/forum?id=IRcv4yFX6z) by Tsung-Wei Ke, Sangwoo Mo and Stella X. Yu.  Authors train CAST by enforcing hierarchical consistency across increasingly large superpixels within an image, thereby enforcing intra-image consistency. The CAST model has the advantage of being a relatively lightweight while outperforming CLIP in important tasks like semantic segmentation. 



## Conclusion 

Sparse dictionary learning is a promising interpretability tool, but it assumes that a model has encoded meaningful knowledge. Common vision models that generalize poorly to unseen data may not contain sufficient interpretable knowledge for sparse dictionary learning to effectively identify interpretable, monosemantic features. 

In this post I've laid out a hypothesis that applying dictionary learning to a vision model trained for hierarchical understanding, will be more likely to uncover controllable, interpretable features. 

To test this effectively would require first quantifying hierarchical consistency in both a common vision model, like ImageNet or CLIP, and in one of the models optimized for hierarchical consistency, CAST or RE-CLIP. Next, applying sparse dictionary learning on each. Finally, quantifying which of the models has yielded more interpretable features. 
