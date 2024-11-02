# Named Entity Recognition (NER) with Llama 3.2

## Overview

This repository contains a **Named Entity Recognition (NER)** implementation using a **LLaMA 3.2** model, specifically leveraging its autoregressive (decoder-only) architecture. The project demonstrates how to adapt a LLaMA model for NER tasks by disabling causal masking, enabling bidirectional attention, and applying **Low-Rank Adaptation (LoRA)** for fine-tuning. This is a **showcase** project and is not fully optimized or thoroughly tested.

## Features

- **Model**: LLaMA 3.2 (1TB) - a decoder-only transformer-based large language model (LLM).
- **Attention Mechanism**: Causal masking is disabled to allow bidirectional attention, suitable for NER tasks.
- **Optimization**:
  - **LoRA**: Low-Rank Adaptation is used to efficiently fine-tune the model with fewer trainable parameters.
  - **AdamW Optimizer**: The AdamW optimizer is used by default, as implemented in Hugging Face's Transformers library.
  - **Cosine Learning Rate Scheduler**: A cosine learning rate schedule is applied for smoother convergence.

## Dataset

* https://www.kaggle.com/datasets/juliangarratt/conll2003-dataset
