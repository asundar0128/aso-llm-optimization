## ASO LLM Optimization

# Neural Transformer Architectures for Antisense Oligonucleotide (ASO) Efficacy Prediction

This repository contains an inference-ready computational pipeline for predicting the inhibition efficacy of novel antisense oligonucleotide (ASO) candidates using large language models (LLMs) and transformer-based architectures.

This work accompanies the preprint:

Benchmarking Large Language Models for Predicting Therapeutic Antisense Oligonucleotide Efficacy
bioRxiv DOI: https://doi.org/10.64898/2026.02.17.706455

The system is designed to enable rapid computational triaging of ASO candidates prior to experimental validation, reducing the number of sequences requiring costly in-vitro screening.

## Problem Context

Therapeutic antisense oligonucleotide (ASO) development requires evaluation of sequence-level inhibition efficacy prior to downstream experimental validation. Traditional computational screening methods rely on rule-based heuristics or feature-engineered models that may not capture complex sequence-structure relationships.

This repository implements an LLM-based inference pipeline capable of predicting ASO efficacy directly from nucleotide sequence input using zero-shot and few-shot prompting strategies.

## Supported Model Architectures

Models evaluated in this pipeline include:

- LLaMA-2-7B
- GPT-3.5-Turbo
- Galactica-6.7B
- ChemBERTa
- MolFormer

## Datasets

The following ASO datasets were used for model benchmarking:

- PFRED
- openASO
- ASOptimizer

Sequence-efficacy mappings from these datasets are used to support few-shot prompting during inference.

## Pipeline Overview

The ASO-LLM pipeline performs the following steps:

- Accepts nucleotide sequence input in standard ASO format
- Constructs prompt-based inference tasks
- Performs zero-shot or few-shot LLM inference
- Predicts sequence-level inhibition efficacy
- Generates evaluation metrics and candidate scores
- Outputs screening results in structured JSON/CSV format

This enables rapid triaging of candidate ASOs for downstream experimental validation workflows.

## Inference on Novel ASO Candidates

This repository supports inference on previously unseen ASO sequences without retraining.

## Example Usage

python inference/predict.py \
  --sequence "GCACAGAGTCGTAGCTGGCG" \
  --target "RAF1 mRNA" \
  --model llama2 \
  --mode fewshot \
  --output results.json

## Sample Output

{
  "predicted_efficacy": 0.93,
  "confidence": 0.88,
  "recommended": true
}

Predicted scores can be used to prioritize ASO candidates prior to laboratory validation.

## Workflow

1. Input ASO sequences in standard formats.
2. Perform **LLM-based inference**:
   - **Zero-shot prompting** for rapid ASO evaluation.
   - **Few-shot prompting** for context-enriched optimization.
3. Evaluate ASO optimization using bioinformatics metrics (e.g., sequence folding, thermodynamic properties).
4. Generate validation reports, plots, and CSV outputs for downstream analysis.

## Workflow Diagram

<img width="1024" height="1536" alt="ChatGPT Image Feb 22, 2026, 08_51_49 PM" src="https://github.com/user-attachments/assets/185b0f97-dd52-470d-a5bf-a867bdaa6bac" />

**Figure 3:** High-level workflow showing the LLM-based ASO optimization loop, including sequence input, inference, evaluation, and output generation.

<img width="1024" height="1536" alt="ChatGPT Image Feb 22, 2026, 09_54_10 PM" src="https://github.com/user-attachments/assets/6892550b-efc4-4e62-8528-20cb92395603" />

## ASO Optimization: Zero-Shot & Few-Shot Prompting

After the main workflow, we explore how different prompting strategies affect ASO prediction and optimization.

## Zero-Shot & Few-Shot Prompting

**Zero-Shot Prompting**  
In zero-shot prompting, the model predicts ASO efficacy or generates optimized sequences **without prior examples**. The model relies solely on its pre-trained knowledge to make predictions. This is useful for rapid evaluation when labeled data is limited.

**Few-Shot Prompting**  
Few-shot prompting provides the model with a **small number of example sequences** and their known efficacy scores before asking it to predict new ASOs. By giving contextual examples, the model can better understand the task and produce more accurate predictions. Few-shot prompting often results in higher-quality ASO candidates, especially for specialized domains.

## Pipeline-Specific Behavior

**PFRED**  
- *Zero-Shot:* Quickly predicts ASO efficacy from input sequences but may miss nuanced sequence-context relationships.  
- *Few-Shot:* Leverages a few example sequences to improve prediction accuracy, capturing subtle patterns in nucleotide arrangements.

**OpenASO**  
- *Zero-Shot:* Provides baseline sequence optimization without prior examples; suitable for rapid screening.  
- *Few-Shot:* Uses context from example sequences to enhance optimization, often yielding higher predicted efficacy and more reliable candidate ASOs.

**ASOptimizer**  
- *Zero-Shot:* Generates initial ASO predictions directly from SMILES or RNA sequences; may produce broader variability.  
- *Few-Shot:* Incorporates sample ASO-efficacy mappings to refine predictions, reducing error and improving alignment with experimental expectations.

> Across all pipelines, few-shot prompting consistently improves model performance by providing **task-specific context**, whereas zero-shot is faster and requires no prior labeled data.

## Repository Structure

data/              Dataset loaders and preprocessing  
models/            Model interfaces  
prompts/           Prompt templates  
training/          Cross-validation logic  
eval/              Metrics and evaluation  
inference/         Candidate screening pipeline  
reports/           Generated plots and CSV outputs  

## Dependencies

- Python 3.8+
- PyTorch / TensorFlow
- bioctfl (for ASO sequence processing)
- pandas, numpy, matplotlib, seaborn
- Jupyter Notebook

Optional:

- GPU support for faster inference
- Docker for containerized deployment

## Environment Setup

1. Clone repository

git clone https://github.com/asundar0128/aso-llm-optimization.git
cd aso-llm-optimization

2. Install dependencies

pip install -r requirements.txt

## Example Output

- Predicted ASO inhibition efficacy scores
- Zero-shot vs Few-shot performance comparison
- Candidate prioritization reports
- Evaluation logs for regression and classification accuracy

## Future Work

- Chain-of-Thought prompting for sequence reasoning
- Scaling few-shot context size
- Integration with experimental ASO validation pipelines
- Evaluation on additional transformer-based models

## System Architecture

## Core Methodology

1. **Background Research**
   - Conducted a comprehensive evaluation of Neural Transformer architectures for efficiency and accuracy in gene therapy and drug discovery pipelines.
   - Surveyed relevant bioinformatics and ASO research literature to guide architecture selection.

2. **Model Selection**
   - Models evaluated: **LlaSMol, T0pp, Mistral-7B**.
   - Models used in practice: **LLaMA2, GPT-3.5-Turbo, Galactica-6.7B** for their superior performance in biological sequence reasoning and ASO optimization tasks.

3. **Optimization**
   - Achieved significant improvements in **R²** and **RMSE** scores through **zero-shot** and **few-shot prompting** strategies.
   - Optimizations guided by relevant bioinformatics principles to ensure predictive and experimental utility.

## Performance & Evaluation

- **Efficacy Tracking:** AUC, ROC, MCC (Matthews Correlation Coefficient) to assess classification performance.
- **Regression Accuracy:** RMSE, R² for sequence-level prediction accuracy.
- Results are documented in a formal publication with **multi-metric evaluation** for robust performance benchmarking.

## Sample Prompts and Inhibition Efficacy Scores

Entry 12
Prompt: [DNA_START]GCACAGAGTCGTAGCTGGCG[DNA_END]
Target gene: Rattus mRNA for vascular type-1 angiotensin II receptor
Inhibition efficacy score: 0.93

Entry 35
Prompt: [DNA_START]TGGGCGGCGCCCCTCCTCCT[DNA_END]
Target gene: Homo sapiens RAF1 mRNA
Inhibition efficacy score: 0.998

Entry 67
Prompt: [DNA_START]GTTACCTCCTCGTTTCTTCT[DNA_END]
Target gene: Homo sapiens P-glycoprotein (PGY1) mRNA
Inhibition efficacy score: 0.99

Entry 105
Prompt: [DNA_START]GTTGGAGTCGG[DNA_END]
Target gene: Human ICAM-1 mRNA
Inhibition efficacy score: 0.967

Entry 181
Prompt: [DNA_START]GAATTTTACGGACCC[DNA_END]
Target gene: Homo sapiens VCAM1, transcript variant 1, mRNA
Inhibition efficacy score: 0.993

## Evaluation Metrics

Model performance is evaluated using:

- RMSE
- R²
- ROC-AUC
- Matthews Correlation Coefficient (MCC)

Both regression and classification performance are reported in the associated preprint.

## References

- LLaMA-2: https://arxiv.org/abs/2307.09288
- Galactica: https://arxiv.org/abs/2211.09085
- PFRED: https://www.ebi.ac.uk/seqdb/pfred
