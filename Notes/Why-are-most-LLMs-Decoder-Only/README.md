# Why are most LLMs Decoder Only

Recent advancements in Large Language Models (LLMs) have captured significant attention due to their potential in natural language processing (NLP). Understanding these developments requires a dive into various architectural designs, mathematical principles, and engineering optimizations. This article explores the evolution of LLM architectures, their training methodologies, and performance metrics.

## Overview of Language Model Architectures

### Encoder and Decoder

- **Encoder**: Transforms input data into a condensed representation, capturing essential information. For instance, in a translation task, an encoder processes an English sentence into a vector representing its linguistic features and meaning.
- **Decoder**: Generates output from the encoded representation. In translation, the decoder converts the encoded English sentence into its French equivalent.

### Encoder-Only Models

- **Example**: BERT-based models
- **Pretraining Approach**: Masked Language Modelling (MLM)
- **Use Case**: Tasks requiring deep understanding of input data, such as classification, sentiment analysis, and information extraction.

### Decoder-Only Models

- **Example**: GPT, XLNet
- **Pretraining Approach**: Next Token Prediction
- **Use Case**: Generative tasks, predicting subsequent text based on context in an auto-regressive fashion.

### Encoder-Decoder Models

- **Example**: T5, BART, Google Gemini (probably)
- **Pretraining**: Task-dependent
- **Use Case**: Tasks involving both understanding and generating data, encoding input sequences into internal representations and decoding them into output sequences.

## Comparing Architectures: Causal Decoder (CD) vs Encoder-Decoder (ED)

### Performance Analysis

Research comparing various combinations of architecture and pretraining approaches has shown that:

- **Causal Decoder-only models**: Strong zero-shot generalization after self-supervised pretraining.
- **Encoder-Decoder models**: Best performance with masked language modeling followed by multitask finetuning.

### Cost of Training

- **Encoder-Decoder (ED) Models**: Require expensive multitask finetuning on labeled data, especially for larger models.
- **Decoder-only (CD) Models**: Achieve strong performance with zero-shot generalization using self-supervised learning on a large-scale corpus.

## Emergent Abilities in Large Language Models

Emergent abilities refer to new, sophisticated capabilities that arise naturally as models scale in size and complexity. These abilities enable LLMs to perform complex reasoning, such as extracting structured knowledge from unstructured text. While emergent abilities reduce the performance gap between ED and CD models, they do not necessarily favor one architecture over the other.

## In-Context Learning from Prompts

Prompt engineering methods, like providing few-shot examples, help LLMs understand context or tasks. In-context learning can be seen as having a similar effect to gradient descent, updating the attention weight of zero-shot prompts. This effect is more straightforward for decoder-only models as it does not need to be translated into an intermediate context first.

## Efficiency Optimization

In decoder-only models, the Key (K) and Value (V) matrices from previous tokens can be reused for subsequent tokens, improving efficiency by avoiding recomputation. This caching mechanism facilitates faster generation and lower computational costs during inference.

## Autoregressive vs Bidirectional Attention

- **Autoregressive Attention (Decoder-only)**: Constrained to a lower triangular form due to causal masking, maintaining full rank status for stronger expressive capability.
- **Bidirectional Attention (Encoder-Decoder)**: Does not guarantee full rank status, potentially limiting performance. However, after sufficient training, both architectures achieve similar objectives.

## Conclusion

Decoder-only architectures are popular due to their simplicity, good zero-shot generalization, and lower training costs. Although both decoder-only and encoder-decoder architectures have their strengths, there is no conclusive evidence that one is superior to the other in terms of final performance. Future advancements, such as Google Gemini, indicate that encoder-decoder models can work as well, if not better, in certain tasks, especially when incorporating multimodal capabilities. Understanding these architectural nuances provides valuable insights into the evolution and future direction of LLMs.
