
# A Comparative Analysis of Transformer Models for Code Generation

CS5814 - Intro to Deep Learning Final Project (Spring 2022)

 Source code generation from natural language is an integral problem of software development. In recent times, deep learning has taken critical steps towards solving this problem by introducing various Transformer architectures that can efficiently convert natural language (NL) to programming language (PL). In this paper, we have attempted to conduct a comparative study of the performance between four such Transformer models; [CodeBERT](https://doi.org/10.18653/v1/2020.findings-emnlp.139), [CodeGPT](https://arxiv.org/abs/2102.04664), [PLBART](https://doi.org/10.18653/v1/2021.naacl-main.211) and [CodeT5](https://arxiv.org/abs/2109.00859) for the downstream task of code generation. We attempt to fine-tune these pre-trained models on two different programming languages, Python and SQL and compare the results with the aim of finding the most effective model for the NL to PL task. We evaluate the accuracy of each trained transformer model utilizing the [CodeBLEU metric](https://github.com/microsoft/CodeXGLUE/tree/main/Code-Code/code-to-code-trans/evaluator/CodeBLEU). After evaluation, we concluded that the best for SQL programming language with a CodeBLEU score of 16.46, and CodeT5 performed the best for Python programming language with a CodeBLEU score of 18.50. With enough computation resources and time, the CodeBLEU scores for both these models can be improved to reach the benchmark scores. 

## Tech Stack

This project was primarily implmented in the Jupyter Lab enviornment. 

Python Libraries: pytorch, Scikit-Learn, transformers, SciPy

## Run Locally

Clone the project

```bash
  git clone https://git.cs.vt.edu/suchiths/cs5814-codegen.git
```

Go to the project directory

```bash
  cd cs5814-codegen
```

Install dependencies

```bash
  pip install -r requirements.txt
```

Extract Data

```bash
  tar -xzvf trained-models.tar.gz
```
## Dataset

The dataset that has been used in this experiment is the [Stack Overflow Question Code Dataset](https://doi.org/10.1145/3178876.3186081). The dataset consists of approximately hundred and forty eight thousand Python and hundred and twenty thousand SQL domain question code pairs. These question code pairs are of two kinds, single answer and multi-answers. For the purposes of the experiment only the single answer question-code pairs which contained 85K thousand python and 75K SQL question-code pairs were chosen. Although abundant, we discovered in the course of experimentation on an initial model that it would have been too large for timely training given the computing power and time restrictions in the ArcOne environment. Most of the transformers models we proposed for this experiment have a cap on the maximum sequence length, which requires us to truncate the input length, so we decided to use the removal question-code pairs with questions longer than 30 tokens and codes longer than 200 tokens, when tokenized with the RobertaTokenizer, as our initial data reduction strategy. Following the application of the first filter, we were left with 56K python question-code pairs (70% of the original) and 60K SQL question-code pairs (80%). Once again through empirical testing, we found the dataset was still too computationally expensive, but 40K would not be. Using a strategy of uniform random sampling, we chose 40K question-code pairs from both the python and SQL dataset.
## Pre-Trained Models

Each of the models (CodeBERT, CodeGPT, CodeT5 & PLBART) we trained (seperately) on the python and SQL datasets are available through [GoogleDrive](https://drive.google.com/uc?export=view&id=1BQLaiamdwrvwBTVcdTS8JQZNyg4ukenu).

## Authors

- Suchith Suddala - [@suchith3004](https://www.github.com/suchith3004)
- Aritra Majumdar - [@aritram21](https://git.cs.vt.edu/aritram21@vt.edu)

## Appendix

The primary source code and branch history for this project is located at https://git.cs.vt.edu/suchiths/cs5814-codegen.