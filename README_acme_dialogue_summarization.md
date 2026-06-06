# Acme Communications: AI-Powered Dialogue Summarization

## Project Overview

Acme Communications is facing a common messaging-platform challenge: users return to long group chats and struggle to identify the most important details. This project builds a machine-learning proof of concept that automatically summarizes dialogue conversations into concise, useful summaries.

The project uses the SAMSum dataset, which contains messenger-style conversations paired with human-written summaries.

## Business Problem

Information overload in group chats can cause users to miss important updates, decisions, deadlines, and action items. This can reduce user satisfaction and engagement. Automated summarization can help users catch up faster and make conversations easier to navigate.

## Technical Approach

The notebook implements:

1. SAMSum data loading and exploration
2. Dialogue preprocessing
3. Baseline summarization using a BART-family model
4. Fine-tuning of T5-small on SAMSum
5. ROUGE evaluation
6. Latency analysis
7. Human evaluation rubric
8. Qualitative error analysis
9. Priority message extraction as a product extension
10. Saved model loading and inference verification

## Model Architecture

The project uses transformer-based sequence-to-sequence models:

- Baseline: `sshleifer/distilbart-cnn-12-6`
- Fine-tuned model: `t5-small`

T5-small was selected for fine-tuning because it is practical for a student project while still demonstrating encoder-decoder transformer summarization.

## Evaluation

The project evaluates performance using:

- ROUGE-1
- ROUGE-2
- ROUGE-L
- ROUGE-Lsum
- Average generation latency
- Human evaluation rubric
- Qualitative error analysis

## Product Extension

In addition to summarization, the project includes a priority message extraction feature. This identifies possible action items, deadlines, meeting updates, and urgent messages.

## Limitations

- Fine-tuning uses a limited sample size by default for runtime management.
- ROUGE does not fully measure user usefulness or factuality.
- Generative models may hallucinate.
- Priority message extraction is rule-based and should eventually be replaced with a trained classifier.
- Production deployment would require latency optimization.

## Future Work

Future improvements could include:

- Fine-tuning on the full SAMSum dataset
- Comparing additional models such as FLAN-T5, Pegasus, or BART-large
- Building a trained action-item classifier
- Adding hallucination detection
- Optimizing inference speed
- Building a web demo or API endpoint
- Conducting user testing

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Then open and run:

```bash
acme_dialogue_summarization_project_FINAL.ipynb
```

The notebook is designed for Google Colab or a local Python environment with internet access. GPU is recommended for fine-tuning.

## Repository Contents

```text
acme_dialogue_summarization_project_FINAL.ipynb
README.md
requirements.txt
saved_samsum_t5_model/   # Created after running notebook fine-tuning cells
```