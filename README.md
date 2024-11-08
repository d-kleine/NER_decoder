# Named Entity Recognition (NER) with Llama 3.2

## Overview

This repository contains a **Named Entity Recognition (NER)** implementation using a **LLaMA 3.2** model using *HuggingFace*, specifically leveraging its autoregressive (decoder-only) architecture. The project demonstrates how to adapt a LLaMA model for NER tasks by disabling causal masking, enabling bidirectional attention, and applying **Low-Rank Adaptation (LoRA)** for fine-tuning. 

> [!IMPORTANT]
> This is a showcase project and thus not fully optimized or thoroughly tested. The finetuned model in its current state overfits, meaning it performs well on the training set but struggles to generalize to new, unseen data. This overfitting likely results from the model's complexity relative to the dataset size or insufficient regularization during fine-tuning. Further steps such as hyperparameter tuning, and more robust regularization techniques would be necessary to improve generalization. Additionally, the model's bidirectional attention mechanism, enabled by disabling causal masking, may require further refinement to balance its performance across both training and evaluation datasets.

## Purpose
Traditionally, encoder-only models like BERT have dominated NER tasks due to their ability to process input text bidirectionally, capturing rich contextual information. However, by removing the causal mask in LLaMA, we enable it to leverage bidirectional context while maintaining its strengths in generative tasks, making it a versatile solution for NER. Compared to encoder-only models like BERT, LLaMA offers several advantages:
* scalability: more effectively with larger datasets and parameters, enabling better performance on zero-shot and few-shot tasks. 
* its architecture can handle both generative and understanding tasks, making it more flexible. 

This makes LLaMA a (potentially) superior choice when both text generation and understanding are needed, especially in large-scale applications.

## Features

- **Model**: LLaMA 3.2 (1B) - a decoder-only transformer-based large language model (LLM).
- **Attention Mechanism**: Causal masking is disabled to allow bidirectional attention, suitable for NER tasks.
- **Optimization**:
  - **LoRA**: Low-Rank Adaptation is used to efficiently fine-tune the model with fewer trainable parameters.
  - **AdamW Optimizer**: The AdamW optimizer is used by default, as implemented in Hugging Face's Transformers library.
  - **Cosine Learning Rate Scheduler**: A cosine learning rate schedule is applied for smoother convergence.

## Dataset

* https://www.kaggle.com/datasets/juliangarratt/conll2003-dataset

## NER Tagging Structure

The **NER (Named Entity Recognition) tags** used in this project follow the **BIO tagging scheme**, which is commonly used in NER tasks to label entities in text. Here's a breakdown of what each tag means:

### **Tag Structure**
- **B-**: Indicates the beginning of a named entity.
- **I-**: Indicates that the token is inside a named entity but not at the beginning.
- **O**: Represents tokens that are not part of any named entity.

### **Entity Types**
- **PER**: Person (e.g., names of individuals)
- **ORG**: Organization (e.g., companies, institutions)
- **LOC**: Location (e.g., cities, countries, geographical regions)
- **MISC**: Miscellaneous entities that don't fall into the other categories (e.g., events, nationalities)

## Setup Instruction

1. **Ensure Python 3.11 is Installed**
   - Verify that Python 3.11 is installed on your system by running:
     ```bash
     python3.11 --version
     ```
   - If Python 3.11 is not installed, you will need to install it first. This can typically be done through a package manager or by downloading from the official Python website.

2. **Navigate to Your Project Directory**
   - Open your terminal and change to the directory where you want to set up your project:
     ```bash
     cd /path/to/your/project
     ```

3. **Create a Virtual Environment**
   - Use the `venv` module to create a virtual environment:
     ```bash
     python3.11 -m venv .venv
     ```
   - This command creates a new directory named `.venv` in your project folder, which contains the virtual environment.

4. **Activate the Virtual Environment**
   - Activate the virtual environment to start using it:
     - On macOS and Linux:
       ```bash
       source .venv/bin/activate
       ```
     - On Windows:
       ```bash
       .venv\Scripts\activate
       ```

5. **Upgrade pip**
   - Before installing packages, ensure you have the latest version of `pip`:
     ```bash
     pip install --upgrade pip
     ```

6. **Install Packages from requirements.txt**
   - Use `pip` to install all required packages listed in your `requirements.txt` file:
     ```bash
     pip install -r requirements.txt
     ```

7. **Deactivate the Virtual Environment (Optional)**
   - Once you are done working in the virtual environment, you can deactivate it by simply running:
     ```bash
     deactivate
     ```