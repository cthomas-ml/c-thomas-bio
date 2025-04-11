---
title: "Mitigating LLM Sycophancy"
categories:
  - Artificial Intelligence
tags:
  - Alignment
  - Safety
toc: true
toc_sticky: true
---

<figure style='display: table'>
  <img src="{{site.baseurl}}/assets/images/Chatbot.png" alt="Sycophants are easily manipulated.">
  <figcaption style='display: table-caption; caption-side: bottom;'>
  A sycophantic AI is easily manipulated by the user to give an incorrect response. The model provides the correct answer to a neutral prompt, but prioritizes agreement over correctness when the prompt contains an incorrect opinion.  </figcaption>
</figure>



## Overview

*This is the second of a two-part series of posts on LLM sycophancy.*

In my [last post]({{site.baseurl}}/artificial%20intelligence/sycophancynb) I showed how to  probe a model for sycophancy. I demonstrated how to identify scenarios in which it arises, and datasets, output formats, and prompt manipulations that most easily encourage the model to output an incorrect or inconsistent response. 

In this post, I'll dive into two recent approaches that aim to mitigate LLM sycophancy, both of which depend on automated prompt manipulation. Finally, I lay out how either technique would be used in production.  


### Summary 

- Compare two recent methods to address sycophantic behavior in LLMs : 
[Simple synthetic data reduces sycophancy in large language models](https://arxiv.org/abs/2308.03958) involves generating randomly (in)correct opinionated prompts for model finetuning.
 [Discovering Latent Knowledge in Language Models Without Supervision](https://arxiv.org/abs/2212.03827), aka Contrast Consistent Search (CCS), selects a mid-model layer and trains a probe to distinguish truthful from untruthful latent representations.
  - **Similarities**
    - Both methods leverage automated prompt manipulation to generate training data.
    - In generating prompt manipulations, both methods make assumptions about the type of opinion that will be expressed.
    - Both papers were limited to multiple choice questions, but the synthetic data approach may be extendable to summary responses.
  - **Differences**
    - The CCS probe is light-weight and easy to train or update if unexpected opinions arise, where finetuning requires a large GPU and long train-time and would be hard to adapt.
    - CCS does not change the original model and doesn't risk knowledge loss. The CCS probe acts on unchanged model representations, where synthetic-data-finetuning will change results for all queries.
    - CCS on an encoder-decoder model only leverages the encoder and doesn't allow the query to fully pass through the model.
- Suggest methods to leverage these approaches in real-life scenarios.


## Mitigating Model Sycophancy 

### Approaches

I will dig into two recent publications of methods that might help reduce large language model sycophancy. The first is [Simple synthetic data reduces sycophancy in large language models](https://arxiv.org/abs/2308.03958), and the second is [Discovering Latent Knowledge in Language Models Without Supervision](https://arxiv.org/abs/2212.03827).  Both papers link to GitHub repos that were used heavily in this study, and I provide a high-level summary in the Approaches section in the sidebar.

[Simple synthetic data reduces sycophancy in large language models](https://arxiv.org/abs/2308.03958), from Google DeepMind in Feb, 2024, shows that as models grow larger, they exhibit increasing tendency to agree with an incorrect prompt despite knowledge of the correct response. The paper addresses this sycophancy with supervised fine-tuning on lots of generated data in which the prompt correctness is random but the ground-truth is accurate, effectively training the model to ignore extraneous information provided in a prompt and provide a known, correct answer. The paper demonstrates that they can improve model accuracy on prompts similar to those used in fine-tuning. The approach requires the engineers to (1) know what types of prompts to protect against, and (2) generate significant volumes of training data to combat each type.

[Discovering Latent Knowledge in Language Models Without Supervision (CCS)](https://arxiv.org/abs/2212.03827) from UC Berkeley at ICLR 2023, focuses instead on extracting the correct response from the model's latent representations. This work also requires prompt manipulation. In this case, an incoming prompt is manipulated in two different ways, yielding one phrase for each possible model response. Each phrase is then passed through part of the model to calculate the latent representation vectors. A lightweight probe is then trained on the latent representations by minimizing the sum of the consistent loss, ensuring that the total probability of responses will sum to 1, and the informative loss, which pushes probabilities towards their extremes of 0 and 1. The approach requires the engineers to (1) know how to manipulate prompts to elicit opposing embeddings, and (2) train the probes for the types of questions that are expected. 
<!-- **Note:** There is an updated repo from Berkeley, rebranding this work as ['Eliciting Latent Knowledge'](https://github.com/EleutherAI/elk). -->



### Quantifying sycophancy

My [last post]({{site.baseurl}}/artificial%20intelligence/sycophancynb) starts with a definition and simple exploration of sycophancy in LLMs. Going deeper, I generated two synthetic language datasets using the [synthetic data github repo](https://github.com/google/sycophancy-intervention). I also used an open-source dataset of product reviews.  For all datasets, I processed the prompts to include or exclude incorrect user opinions and limit the model response to multiple choice (Agree or Disagree), using the code shared in my [last post]({{site.baseurl}}/artificial%20intelligence/sycophancynb).  I continued working with the [google/flan-t5-xxl](https://huggingface.co/google/flan-t5-xxl) model, because it is similar to the models used in the papers above. 

In the multiple-choice setting, I tested model accuracy with and without incorrect opinions included in the prompts. The model generally prefers to agree with an opinion expressed in the prompt, even if it answers correctly when no opinion is included. However, it is much easier to elicit sycophancy in the synthetic math dataset than in the IMDB dataset. 


| Dataset | No opinion | Incorrect opinion included  |
---------------|------------|-----------|
| Synthetic Math  |    100%    |     0%    |
| Synthetic Linguistics  |     62%    |     11%   |
| IMDB         |     96%    |     60%   |


When prompted by the synthetic linguistics data with opinions removed, the model performance was only slightly better than random. The aim of finetuning on this dataset is to train the model to prioritize truthfulness over sycophancy. Here I define 'truthfulness' as reflective of the model's learned knowledge. 

To ensure the model will prioritize its knowledge over agreement, the dataset is filtered to include only the 62% of samples that the model answers correctly when opinions are removed. These examples are identified as ones where the model knows the correct answer and can be trained to ignore opinions.

But the synthetic linguistics prompts are long and convoluted and the questions are 2-choice, so getting the right answer doesn't mean the model knows the right answer. In many cases that pass through the filter, the model doesn't have learned knowledge to prioritize. Instead, it is finetuned on meaningless phrases that contain opinions. **Finetuning on these data may reduce sycophancy at the cost of model performance on unrelated, meaningful tasks.** 


I also found that the **sycophantic tendency of the model is sensitive to how an opinion is phrased, the requested output task (classification vs. summarization), and the specifics of the dataset.** For example, in the math dataset the model exhibits complete sycophancy in the multiple choice setting, but not in summary mode, whereas in the IMDB dataset, it is less prone to exhibit sycophancy in the multiple choice setting and can be tricked more readily in summary mode. 

**The sensitivity of the model's sycophancy to the specifics of prompt manipulation will impact both mitigation methods.** Both methods involve prompt editing to create training data and may thus be vulnerable if manipulations don't capture the target sycophancy-inducing prompts. In CCS, the aim is to generate model embeddings for *both* answers to a given question. A probe is trained to contrast those two embeddings and determine which one is the 'truth.' In finetuning with synthetic data, the dataset is generated with a predefined format. 

### Training sycophancy mitigators

<span style="color:grey"> 
*This section benefited greatly from the well-documented and easy-to-follow [CCS GitHub repo](https://github.com/collin-burns/discovering_latent_knowledge).
Note that all experiments in this section were performed with low number of samples, and to get reliable results would require re-running at higher N.  Stay tuned* </span>.

In CCS every prompt gets manipulated into two prompts - one representing each answer of the two-choice question. The two samples are then passed through the model to calculate an embedding vector. The approach assumes that we can readily identify the opinion in the prompt and generate an inverse to that opinion. 

From that point I used the vectors and their labels to train a supervised logistic regression model to determine whether the vectors are distinguishable. If they weren't, the unsupervised CCS method wouldn't have a chance. I then removed the labels to train the CCS probe and report the following response accuracies. 



| Dataset       |     Logistic Regression on Latents| CCS  result |
--------------------------------|----------------|----------------|
| Simple Math (synth)           |      100%      |     100%       |
| Linguistics (synth, filtered) |       58%      |      60%       |
| IMDB                          |       92%      |      88%       |

CCS should ideally restore performance to the no-opinion case. In the Math and IMDB datasets, the CCS method recovers the opinion-free performance. In the synthetic linguistics dataset, even logistic regression failed to distinguish positive from negative embeddings.  The poor separation in latent space supports the suspicion that the model is being finetuned on prompts that don't have meaning to the model.

Next I examined how well the approach generalized to other datasets. A mitigation method would be most useful if I could train a model using one dataset, and apply it on new, unseen datasets. 


| Method     |    Train set      |     Test set       |Response Accuracy|
-------------|-------------------|--------------------|----------------|
| CCS |  50% Linguistics  |       50% Linguistics     |   64%    |
| CCS |    Linguistics    |           Math (synth)    |   100%   |
| CCS |    Linguistics    |               IMDB+       |   82%    |

When training on the linguistics dataset, some but not all accuracy is recovered when testing on the opinionated-IMDB (ie. IMDB+) dataset. 


## Protecting against model sycophancy

To effectively leverage either the CCS or finetuning on synthetic data method, one would prepare a trained probe or finetuned model using a dataset selected to protect against the sycophantic behavior of interest.  

A deployed model might behave as follows. 

With CCS, given a trained probe, 
```
1. Receive a human-generated prompt with an opinion stated.
2. Generate the affirmative and negative prompts on the fly.
3. Calculate embeddings for both prompts and use the probe to select correct embedding.
4. Find the response. In the multiple choice case, this is simply the label for the embedding. For a summary response, pass the correct embedding through the rest of the model to generate.
5. Return response 
```

With a model finetuned on synthetic data,
```
1. Receive a human-generated prompt with an opinion stated.
2. Return response.
```

The finetuned model has a simpler and less-flexible inference time application. 

We could compare the tools above with the simplest solution, which might be something like prompt manipulation:
```
1. Receive a human-generated prompt with an opinion stated.
2. Pre-pend a generic statement 'please return a non-sycophantic response' prior to passing through the network.
3. Return response.
```

## Open questions 

- How much relevant knowledge is lost in each approach? 
- Where in the model is sycophancy happening? In both the math and IMDB datasets, tendency towards sycophancy is different in summary and multiple choice scenarios.
- Would Anthropic's synthetic dataset be useful in comparing these approaches? 


## About the project

This project was contributed as part of the 2024 BlueDot Alignment course, with gratitude to my collaborators. Special thanks to Aaron Scher for thoughtful insights and resources. 
<!-- 'm also grateful to the authors of both papers, who made very accessible code and Hugging Face, which seems to make everything possible.  -->