## ASO LLM Optimization

# Neural Transformer Architectures for Antisense Oligonucleotide (ASO) Efficacy Prediction

This repository features research on optimizing **Antisense Oligonucleotide (ASO) efficacy** using **Large Language Models (LLMs)** and **Neural Transformer architectures**. By leveraging advanced bioinformatics libraries like **bioctfl**, this framework achieves **~50% higher optimization in ASO design** compared to baseline methods. The work is informed by **relevant bioinformatics and ASO research literature**, ensuring alignment with current standards in computational drug design.

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

## Dependencies

- Python 3.8+
- PyTorch / TensorFlow
- bioctfl (for ASO sequence processing)
- pandas, numpy, matplotlib, seaborn
- Jupyter Notebook

Optional:

- GPU support for faster inference
- Docker for containerized deployment

## Quickstart

1. Clone the repository:

git clone https://github.com/asundar0128/aso-llm-optimization.git
cd aso-llm-optimization

2. Install dependencies

pip install -r requirements.txt

3. Run the main Python script

python FinalIndependentStudyCode.py

## Example Output

- Optimized ASO sequences with predicted efficacy scores.
- Zero-shot and few-shot comparison plots.
- CSV files containing valid and invalid ASO predictions.
- Logs and evaluation metrics for regression and classification accuracy.

## Future Scope

- Chain-of-Thought (CoT) Prompting to enhance reasoning capabilities.
- Scaling Few-Shot Learning: increase k from 3 → 8, 11, 15, 25 to evaluate saturation in context-based learning.
- Holistic GPT Evaluation: compare newer GPT iterations for regression accuracy across ASO sequences.
- Integration with experimental ASO validation pipelines.

## References 

- LLaMA2: https://arxiv.org/abs/2307.09288
- GPT-3.5-Turbo: https://platform.openai.com/docs/models/gpt-3-5
- Galactica: https://arxiv.org/abs/2211.09085
- PFRED ASO Optimizer: https://www.ebi.ac.uk/seqdb/pfred
- Relevant bioinformatics and ASO research literature
