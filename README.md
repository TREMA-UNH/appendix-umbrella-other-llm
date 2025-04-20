# appendix-umbrella-other-llm



This repository contains code and resources for reproducing the experiments in **"Does UMBRELA Work on Other LLMs?"**. Our study investigates the generalizability of the UMBRELA LLM Judge evaluation framework across different large language models (LLMs), assessing its effectiveness beyond the original study.

## 📌 Overview
The UMBRELA framework provides a zero-shot, structured prompting approach for generating graded relevance labels. This work explores:
- How different LLMs impact relevance assessment accuracy.
- The effect of model scale on leaderboard rank correlation and per-label agreement.
- The reproducibility of UMBRELA's effectiveness across various LLM families.


## 🤖 Models Evaluated

We evaluated UMBRELA on:

- Flan-T5-Large
- Meta-Llama-3-8B-Instruct
- Meta-Llama-3.3-70B-Instruct-Turbo
- DeepSeek-V3


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

<details>
  <summary>📜 Full Evaluation Command Reference (Click to expand)</summary>

```
python src/main.py \
  --model_id "<MODEL_ID>" \
  --test_qrel_path "<PATH_TO_QREL_FILE>" \
  --queries_path "<PATH_TO_QUERIES_FILE>" \
  --docs_path "<PATH_TO_DOCUMENTS_FILE>" \
  --prompt_mode "<PROMPT_MODE>" \
  --result_file_path "<OUTPUT_RESULT_FILE>" \
  -together (Only if you want to run a model with Together AI API )
```

Example of usage
```
python src/main.py \
  --model_id "deepseek-ai/DeepSeek-V3" \
  --test_qrel_path "./data/dl2020/2020qrels-pass.txt" \
  --queries_path "./data/dl2020/msmarco-test2020-queries.tsv" \
  --docs_path "./data/dl2020/dl2020_document.jsonl" \
  --prompt_mode "zeroshot_bing" \
  --result_file_path "./results/dl20_test_zeroshot_bing_DSV3.txt" \
  -together


```
</details>

## 🔧 Main Arguments

| Argument             | What it means                                      |
|----------------------|----------------------------------------------------|
| `--model_id`         | Model name from HuggingFace (e.g., `deepseek-ai/DeepSeek-V3`) |
| `--prompt_mode`      | Prompt strategy to use (`zeroshot_bing`, etc.)    |
| `--test_qrel_path`   | Path to qrel (ground-truth relevance) file        |
| `--queries_path`     | Path to the file with search queries               |
| `--docs_path`        | Path to the document file                          |
| `--result_file_path` | Where to save the model’s output                   |
| `-together`          | Use Together.ai API to run the model (optional)   |