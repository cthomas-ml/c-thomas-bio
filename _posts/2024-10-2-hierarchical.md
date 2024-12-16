---
title: "Interpreting image models with sparse dictionary learning: a case for hierarchical learning"
categories:
  - Artificial Intelligence
tags:
  - Alignment
  - Safety
---


Recently, Anthropic demonstrated the power of sparse dictionary learning in a large language model. They applied the method to a single embedding layer of a large network to identify a basis of more interpretable features, and demonstrated control of the model output by activating the combination of neurons responsible for single, interpretable features. The work shows that the model is knowledgeable in a meaningful way, but that the meaning is hard to discern from the lower dimensional neuron basis. By identifying a more interpretable, higher dimensional basis, it lays the groundwork for researchers to consider whether the model learned safe, useful relationships and tailor future training accordingly. Not all recovered features appear to be meaningful, which may be due to shortcomings in either the original model or the sparse dictionary learning approach. 

Uncovering meaningful features relies on the model containing enough of them. Language models are trained on concept hierarchies and logical entailment, so we might expect the underlying model to contain meaningful representations and then leverage sparse dictionary leaning to uncover them. 

In contrast, vision models are not trained with any sense of logical entailment or concept hierarchy. While it’s clear that they encode useful information, it may be more difficult to extract and interpret than in sentence encoders that are directly optimized with logical entailment and concept hierarchy. It is nontrivial to train a vision model to leverage the relevant aspects of an image, leading to a reliance on spurious correlations, and it is challenging to quantify this reliance across a dataset.  

Models like AlexNet and even CLIP are known to lack both intra- and inter-image hierarchical consistency, depend on spurious correlations, and generalize poorly to unseen data. The CAST paper shows an example using CLIP, where the model correctly identifies a man holding a fish as a fishing scene, but labels both the man and fish as a fish. While it may be possible to apply dictionary learning to disentangle polysemanticity in such models, the results may not be as clear or exciting as in language models. 

<!-- By applying dictionary learning to a vision model trained for hierarchical understanding, we can examine the impact of concept hierarchies on the effectiveness of the method as a means of uncovering interpretability. 

While exciting results have been recently demonstrated in language models, the results may be less clear in common deep learning models trained on images.  -->

Rather than directly applying a sparse dictionary learning approach to common vision models, I suggest applying sparse dictionary learning to a vision model that has been optimized with consideration for hierarchical understanding, such as CAST (ICLR 2024) or RE-CLIP (ECCV, 2024). The CAST model is trained in such a way that enforces hierarchical consistency across increasingly large superpixels within an image. This has the advantage of being a relatively lightweight model that outperforms CLIP in important tasks like semantic segmentation. The RE-CLIP paper examined concept hierarchy in CLIP, built a metric to quantify it, and fine-tuned on this metric to produce a model with quantitative and qualitative improvement to concept hierarchy in the model’s latent representations. The RE-CLIP model is probably too big to tackle during the program, but I can borrow the metric from the paper to demonstrate the value of hierarchical understanding as a starting point for interpretability. It would also be interesting to examine the concept hierarchy metric in the latents of a common LLM.