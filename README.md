# appendix-umbrella-other-llm



This repository contains code and resources for reproducing the experiments in **"Does UMBRELA Work on Other LLMs?"**. Our study investigates the generalizability of the UMBRELA LLM Judge evaluation framework across different large language models (LLMs), assessing its effectiveness beyond the original study.

## 📌 Overview
The UMBRELA framework provides a zero-shot, structured prompting approach for generating graded relevance labels. This work explores:
- How different LLMs impact relevance assessment accuracy.
- The effect of model scale on leaderboard rank correlation and per-label agreement.
- The reproducibility of UMBRELA's effectiveness across various LLM families.

## 📂 Repository Structure
```
├── prompts/ # Prompt templates for different settings 
│ ├── qrel_fewshot_basic.txt 
│ ├── qrel_fewshot_bing.txt 
│ ├── qrel_zeroshot_basic.txt 
│ ├── qrel_zeroshot_bing.txt 
├── results/ # Stores evaluation outputs 
├── src/ # Source code for processing and evaluation 
│ ├── data_processing.py # Handles input/output
│ ├── main.py # Main script to run the evaluation 
│ ├── make_rubric_format.py # Converts data into rubric-based format 
│ ├── model_utils.py # Functions to load and interact with LLMs 
│ ├── prompts.py # Handles prompt construction 
│ ├── relevance_processors.py 
│ ├── relevance_scoring.py 
├── run_command.sh # Example script for running the evaluation 
└── README.md # Project documentation
```