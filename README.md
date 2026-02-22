# Neural Transformers for Antisense Oligonucleotide (ASO) Design

This repository features research on optimizing Antisense Oligonucleotide (ASO) efficacy using Large Language Models (LLMs) and Neural Transformer Architectures. By leveraging advanced bioinformatics libraries like bioctfl, this framework achieves a 50% higher optimization in ASO design compared to original findings.

# System Architecture

Core Methodology

- Background Research: Conducted an extensive evaluation of Neural Transformer architectures to identify the most efficient models for gene therapy and drug discovery.
- Model Selection: After a holistic evaluation of models including LlaSMol, T0pp, and Mistral-7B, the project primarily utilized LLaMA2, GPT-3.5-Turbo, and Galactica-6.7B for their superior performance in biological sequence reasoning.
- Optimization: Achieved significant improvements in $R^2$ and RMSE scores through strategic zero-shot and few-shot prompting.

# Performance & Evaluation

Research findings were documented in a formal publication analyzing state-of-the-art LLM frameworks. Success was measured using a multi-metric approach:
- Efficacy Tracking: AUC, ROC, and MCC (Matthews Correlation Coefficient).
- Regression Accuracy: Root Mean Square Error (RMSE) and Coefficient of Determination ($R^2$).

# Future Scope

To further refine the accuracy of ASO efficacy binding and reasoning, the following steps are planned:
- Reasoning Capabilities: Implement Chain-of-Thought (CoT) Prompting and re-integrate T0pp, Mistral-7B, and LlaSMol to compare reasoning paths.
- Scaling Few-Shot Learning: Transition from $k=3$ to higher parameters ($k=8, 11, 15, 25$) to determine the saturation point of context-based learning for ASO sequences.
- Holistic GPT Evaluation: Expand the testing suite to include newer GPT iterations for a broader comparison of regression metrics.
