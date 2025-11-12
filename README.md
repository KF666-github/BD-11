# Automated Book Drawing for Audiobook Production:A Benchmark and Comparative Study from Heuristics to LLMs

We revisit the task of speaker attribution in narrative texts from the underexplored perspective of industrial-scale audiobook production, and define Automated Book Drawing (ABD) as a structured solution to meet its unique annotation challenges. Motivated by the high cost and inconsistency of manual annotation in voice acting workflows, we formalize ABD as a multi-class classification task grounded in discourse reasoning. To support systematic research, we introduce BD-11, a highquality Chinese benchmark dataset comprising 58,818 annotated dialogues from 11 diverse web novels, with dialogues categorized into easy and hard cases based on attribution difficulty. We benchmark three representative paradigms: (1) a heuristic method using named entity proximity; (2) a BERT-based Machine Reading Comprehension (MRC) model that treats attribution as a span extraction task; and (3) a prompt-based framework using ChatGPT with zero-shot, few-shot, and chain-of-thought prompting.
# BD-11 Dataset

# Methods
## Heuristic Rule-based Approach
The heuristic method assigns each dialogue to the nearest character mention within a defined context window. Using Named Entity Recognition (HanLP, MSRA NER ELECTRA SMALL ZH), person entities are extracted, and the closest external name to the dialogue is selected as the speaker.

![alt text](./imgs/Heuristic%20Rule-based%20Approach.jpg)

## BERT-based Machine Reading Comprehension Approach
The BERT-based MRC model formulates speaker attribution as a span extraction task: given a paragraph and the question “Who is the speaker of this dialogue?”, the model identifies the speaker’s name as a text span. We fine-tune the Chinese BERT-base model using the HuggingFace Transformers framework, optimizing hyperparameters through grid search on learning rate and batch size based on development set F1.
![Alt Text](./imgs/BERT-based%20Machine%20Reading%20Comprehension%20Approach.jpg)

## LLM-driven Prompt Engineering Approaches
The LLM-based approach uses ChatGPT-3.5-turbo for ABD through prompt engineering. It applies four prompting strategies: Zero-shot, Few-shot, Chain of Thought (CoT), and Self-Consistency to improve reasoning and robustness. The method performs well on long contexts and implicit cues but may yield inconsistent results due to non-deterministic outputs and sensitivity to phrasing.
