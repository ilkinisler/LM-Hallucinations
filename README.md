# LLM Hallucinations 🧠

A curated list of resources, papers, and tools related to **Large Language Models (LLM) and Hallucinations**.

---

## Overview

### Problem Statement
Language models (LMs) frequently produce outputs that are syntactically convincing but factually incorrect or ungrounded in reliable sources. This phenomenon, referred to as hallucination, presents significant challenges in ensuring the reliability, trustworthiness, and practical adoption of AI systems in critical areas such as healthcare, education, and policy-making. The focus is on tracking AI-generated outputs, evaluating their groundedness, and ensuring their faithfulness to reliable sources to distinguish between real data and synthetic outputs

### Key Terms
- **Hallucination**: Outputs generated by a language model that are factually inaccurate or ungrounded in training data or real-world knowledge.
- **Groundedness**: The extent to which an AI's outputs can be traced back to reliable and credible sources.
- **Faithfulness**: The alignment between generated content and the source data it is derived from.
- **Synthetic Language Data**: Text created by AI models rather than written by humans.
- **Traceability**: The ability to track the origin of an AI-generated text and verify its authenticity.

---

## Challenges
- **Defining and Quantifying Hallucination**:
Lack of universally accepted definitions and metrics for hallucination leads to inconsistencies in evaluation and comparison of methods.
- **Detection and Attribution of Hallucination**:
Differentiating between true and synthetic data, especially in large-scale corpora, is challenging.
Language models often blend accurate facts with hallucinations, making detection harder.
- **Evaluation Benchmarks**:
Current benchmarks focus on synthetic tasks but fail to generalize to real-world use cases or specialized domains like healthcare or law.
- **Scalability and Real-Time Analysis**:
Scaling hallucination detection methods to handle the output of state-of-the-art models in real time is computationally intensive.
- **Lack of Grounded Data**:
Models trained on noisy or biased data inherit these flaws, exacerbating hallucination problems.
- **Ethical and Legal Concerns**:
Misidentifying or misattributing content as hallucinated can have legal and reputational implications.

---

## Evaluation Metrics and Benchmarks
### Metrics:
- **Truthfulness**: Measures the percentage of responses that align with factual correctness.
- **Informativeness**: Assesses how relevant and meaningful the responses are while maintaining truthfulness.

- **Precision and Recall**: Measuring how accurately hallucinations are detected.
- **Faithfulness Scores**: E.g., QAGS (Question-Answering Faithfulness Score), where outputs are evaluated against a reference document.
- **Factual Consistency**: Evaluated via human annotations or automated tools like TruthfulQA or FactCC.
- **Groundedness Metrics**: Assess the extent to which generated content is anchored in reliable sources.
### Benchmarks:
- **TruthfulQA**: Benchmark for identifying when models mimic human falsehoods.
     - Composed of 817 questions across 38 diverse categories, including health, law, politics, and finance.
     - Questions are designed to provoke false answers by mirroring misconceptions or errors commonly propagated by humans.

---

## Detection

1. **TruthfulQA**: [Measuring How Models Mimic Human Falsehoods](https://arxiv.org/pdf/2109.07958) (2022) [GitHub](https://github.com/sylinrl/TruthfulQA)
   - **Context**: Focused on evaluating truthfulness in language models.
     - **Details**: Fine-tuned models are specific to TruthfulQA and are not expected to generalize.
   - **Performance**: ~90-95% validation accuracy in truthfulness classification across all model classes using "GPT-judge" (a finetuned model).
   - **Key Findings**: Scaling models alone does not resolve truthfulness issues; fine-tuning and improved objectives are critical. 
   - **License**: Apache-2.0.

Key Findings:
Benchmark Design:

817 questions across 38 categories designed to provoke falsehoods.
Evaluates truthfulness and informativeness.
Performance:

Best model (GPT-3-175B) achieved 58% truthfulness compared to 94% for humans.
Larger models were more prone to falsehoods, highlighting the inverse scaling phenomenon.
Applications:

Detecting hallucinations in AI-generated text.
Assessing reliability for critical applications like healthcare and law.
Informing training strategies to reduce biases.
Traceability:

While not directly focusing on output tracing, the benchmark aids in understanding the origins of imitative falsehoods.
Conclusion:
Scaling models alone does not resolve truthfulness issues; fine-tuning and improved objectives are critical. TruthfulQA is a valuable tool for evaluating and improving model reliability.

---

2. **REALM / ORQA**
- **Context**: Combines masked language models with a differentiable retriever.
- **Details**: Explored only in open-domain extractive QA.
- **Source Code**: [REALM GitHub](https://github.com/), [ORQA GitHub](https://github.com/)
- **License**: Apache-2.0.

---

### 3. **Retrieval Augmented Generation for Knowledge Intensive NLP Tasks** (2020)
- **Context**: Enhances knowledge retrieval for fact-intensive tasks like QA and summarization.
- **Details**: Combines pre-trained parametric memory (BART seq2seq) and non-parametric memory (Wikipedia).
- **Performance**: SOTA performance on Open-Domain QA tasks; grounded outputs via retrieval.
- **Challenges**: Computationally expensive, dependent on retrieval corpus quality.
- **Source Code**: [HuggingFace](https://huggingface.co/).
- **License**: Apache-2.0.

---

### 4. **Retrieval Augmentation Reduces Hallucination in Conversation** (2021)
- **Context**: Focuses on knowledge-grounded conversational tasks.
- **Performance**: SOTA on two knowledge-grounded tasks.
- **Source Code**: [Parl.ai](https://parl.ai/).
- **License**: MIT.

---

### 5. **On Faithfulness and Factuality in Abstractive Summarization** (2020)
- **Context**: Introduces new evaluation frameworks and datasets.
- **Performance**: Textual entailment measures correlate better with faithfulness than standard metrics.
- **Challenges**: High hallucination rates in existing models.
- **Source Code**: [GitHub](https://github.com/).
- **License**: Creative Commons Attribution 4.0 International (CC BY 4.0).

---

### 6. **SITUATEDQA: Incorporating Extra-Linguistic Contexts into QA** (2021)
- **Context**: Open-retrieval QA dataset with temporal and geographical contexts.
- **Performance**: Models struggle with context-dependent answers.
- **Source Code**: [GitHub](https://github.com/).

---

### 7. **SELFCHECKGPT: Zero-Resource Black-Box Hallucination Detection**
- **Details**: A zero-resource hallucination detection method.
- **Source Code**: [GitHub](https://github.com/).

---

### 8. **Reference-Free Hallucination Detection for Large Vision-Language Models**
- **Details**: Uses uncertainty and consistency-based methods without external tools.

---

### 9. **SAC3: Reliable Hallucination Detection in Black-Box Language Models** (EMNLP 2023)
- **Details**: Uses semantically equivalent question perturbations and cross-model response consistency checks.
- **Source Code**: [GitHub](https://github.com/).

---

### 10. **Unsupervised Real-Time Hallucination Detection Based on Internal States** (ACL 2024)
- **Details**: Uses LLM internal states during inference for real-time detection.
- **Source Code**: [GitHub](https://github.com/).

---

### 11. **Detecting Hallucinations in LLM Generation: A Token Probability Approach**
- **Details**: Simple classifiers using token and vocabulary probabilities outperform SOTA outcomes.
- **Source Code**: [GitHub](https://github.com/).

---

### 12. **Hallucination Detection: Discerning Reliable Answers in LLMs**
- **Details**: The RelD discriminator analyzes bilingual Q&A datasets to detect hallucinations.

---

### 13. **Fine-Grained Hallucination Detection and Editing for LLMs**
- **Details**: Retrieval-augmented models like FAVA detect and correct hallucinations effectively.
- **Source Code**: [GitHub](https://github.com/).

---

### 14. **Detecting and Preventing Hallucinations in Vision-Language Models**
- **Details**: Combines fine-grained annotations and visual-textual inputs.

---

### 15. **Leveraging Graph Structures to Detect Hallucinations in LLMs**
- **Details**: Uses Graph Attention Networks (GATs) to detect hallucinations robustly.
- **Source Code**: [GitHub](https://github.com/).

---

## 📄 Licensing
- **Apache-2.0**: [TruthfulQA](https://github.com/), [REALM](https://github.com/), [ORQA](https://github.com/).
- **MIT**: [Parl.ai](https://parl.ai/).
- **Creative Commons Attribution 4.0**: [Faithfulness and Factuality](https://github.com/).

---
