# LM Hallucination Detection 🧠

A curated list of resources, papers, and tools related to **Language Model (LM)  Hallucination Detection Methods**.

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
Current benchmarks focus on synthetic tasks but fail to generalize to real-world use cases or specialized domains.
- **Lack of Grounded Data**:
Models trained on noisy or biased data inherit these flaws, exacerbating hallucination problems.
- **Ethical and Legal Concerns**:
Misidentifying or misattributing content as hallucinated can have legal and reputational implications.

---

## Benchmarks and Evaluation Metrics
1. **TruthfulQA**: [Measuring How Models Mimic Human Falsehoods](https://arxiv.org/pdf/2109.07958) (2022) [GitHub](https://github.com/sylinrl/TruthfulQA)
     - Benchmark for identifying when models mimic human falsehoods.
     - Composed of 817 questions across 38 diverse categories, including health, law, politics, and finance.
     - Questions are designed to provoke false answers by mirroring misconceptions or errors commonly propagated by humans.
          - **Truthfulness**: Measures the percentage of responses that align with factual correctness.
          - **Informativeness**: Assesses how relevant and meaningful the responses are while maintaining truthfulness.

3. **SituatedQA**: [Incorporating Extra-Linguistic Contexts into QA](https://aclanthology.org/2021.emnlp-main.586.pdf) (2021) [GitHub](https://situatedqa.github.io/)
     - Benchmark for evaluating question-answering (QA) systems on context-dependent questions that require consideration of temporal (time-based) and geographical (location-based) contexts.
     - Highlights how traditional QA systems fail to adapt to context-specific scenarios, limiting their reliability in dynamic or globally diverse applications.
          - **Context-Dependent Accuracy**: Common vs. Rare Locations and Updated vs. Stable Facts
          - **Exact Match (EM) Accuracy, Recall, Precision, and F1 Score**

5. **MIND**: [Unsupervised Real-Time Hallucination Detection Based on Internal States](https://arxiv.org/pdf/2403.06448) (ACL 2024) [GitHub](https://github.com/oneal2000/MIND/tree/main)
     - HELM Benchmark, standardizes the evaluation of hallucination detection, providing robust metrics for comparison. It includes outputs from multiple LLMs, with a focus on:
        - Diverse tasks (e.g., summarization, question answering).
        - Internal model states during hallucination-prone scenarios.
    
8. [Fine-Grained Hallucination Detection and Editing for LLMs](https://arxiv.org/pdf/2401.06855) [GitHub](https://fine-grained-hallucination.github.io/)
     - FavaBench Benchmark:
       - Includes ~1,000 fine-grained human judgments on outputs from ChatGPT, Llama2-Chat (70B, 7B), and others.
       - Evaluates hallucination detection across multiple domains, focusing on both detection and correction tasks.


---

## Detection

1. **TruthfulQA**: [Measuring How Models Mimic Human Falsehoods](https://arxiv.org/pdf/2109.07958) (2022) [GitHub](https://github.com/sylinrl/TruthfulQA)
   - **Context**: Focused on evaluating truthfulness in language models. It also presents a benchmark.
     - **Details**: Fine-tuned models are specific to TruthfulQA and are not expected to generalize.
   - **Performance**: ~90-95% validation accuracy in truthfulness classification across all model classes using "GPT-judge" (a finetuned model).
   - **Key Findings**: Scaling models alone does not resolve truthfulness issues; fine-tuning and improved objectives are critical. 
   - **License**: Apache-2.0.

2. [On Faithfulness and Factuality in Abstractive Summarization](https://arxiv.org/pdf/2005.00661) (ACL 2020) [GitHub](https://github.com/google-research-datasets/xsum_hallucination_annotations)
   - **Context**: Examines the reliability of neural abstractive summarization systems, highlighting their propensity to hallucinate content—generating information not supported by the input document. The authors focus on faithfulness and factuality in generated summaries through large-scale human evaluations and propose methods to evaluate and improve model outputs.
   - **Key Findings**: Textual entailment measures better correlate with faithfulness than standard metrics. 
   - **License**: Creative Commons Attribution 4.0 International (CC BY 4.0).

3. **SelfCheckGPT**: [Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models](https://arxiv.org/pdf/2303.08896) (EMNLP 2023) [GitHub](https://github.com/potsawee/selfcheckgpt)
   - **Context**: A zero-resource hallucination detection method. Does not require access to the model's probability distributions nor external databases. If the model is knowledgeable, responses should be consistent; inconsistent responses indicate hallucinations.
     - **Details**: Compares the original response with multiple stochastically sampled responses using methods like BERTScore, question-answering, and natural language inference (NLI).
   - **Strenghts**: Works without external databases, making it suitable for APIs like ChatGPT.
   - **Metrics**:
     - Sentence-Level Hallucination Detection: Measures how effectively SelfCheckGPT detects non-factual sentences.
     - Passage-Level Factuality Assessment: Ranks passages based on their overall factuality.
   - **License**: MIT.

4. **SAC3**: [Reliable Hallucination Detection in Black-Box Language Models](https://arxiv.org/pdf/2311.01740) (EMNLP 2023) [GitHub](https://github.com/intuit/sac3)
   - **Context**: Builds on the concept of self-consistency checks by adding semantic and cross-model evaluations. The approach addresses two types of hallucinations: question-level (misunderstandings of the input question) and model-level hallucinations (inaccuracies due to the model's internal limitations).
     - **Details**: Uses semantically equivalent rephrasing of questions and compares responses across different models to detect inconsistencies.
   - **Key Findings**:
     - Limitations of Existing Methods: Standard self-consistency checks (e.g., sampling-based methods) often fail to detect certain types of hallucinations, particularly those stemming from: (1) Ambiguous or rephrased questions or (2) Model-specific biases or limitations.
   - **Performance**: SAC3 outperforms prior methods in detecting hallucinations, particularly in challenging cases involving question rephrasings or different model architectures. Makes QA systems more robust to question phrasing and contextual ambiguities. Extends beyond QA to any generative task requiring factual reliability, such as summarization or information retrieval.
     - **Factuality Assessment**: Measures consistency with external knowledge or human evaluations.
     - **Response Consistency**: Evaluates agreement across different models or question perturbations.
   - **License**: Apache-2.0.

5. **MIND**: [Unsupervised Real-Time Hallucination Detection Based on Internal States](https://arxiv.org/pdf/2403.06448) (ACL 2024) [GitHub](https://github.com/oneal2000/MIND/tree/main)
   - **Context**: Uses LLM internal states during inference for real-time detection. It also presents HELM, a benchmark.
      - **Details**: Uses a multi-layer perceptron (MLP) to classify hallucinations based on token embeddings during the inference process.
   - **Strengths**: Real-time detection reduces computational overhead, and its unsupervised nature eliminates the need for labeled data.


6. [Detecting Hallucinations in LLM Generation: A Token Probability Approach](https://arxiv.org/pdf/2405.19648) (May 2024) [GitHub](https://github.com/Baylor-AI/HalluDetect)
   - **Context**: A supervised learning approach for detecting hallucinations in outputs generated by large language models (LLMs). The approach is lightweight, using minimal features derived from token probabilities, and does not require the hallucination detection model to be the same as the LLM that generated the content.
      - **Details**:
        - Token probabilities and vocabulary distributions are collected for the generated text.
        - Features derived from these probabilities are fed into a supervised learning model (a simple classifier) to detect hallucinations.
   - **Conclusion**: A scalable, efficient, and accurate method for hallucination detection
   - **License**: MIT.

7. [Hallucination Detection: Robustly Discerning Reliable Answers in Large Language Models](https://arxiv.org/pdf/2407.04121) (Jul 2024)
   - **Context**: RelD, a robust discriminator for detecting hallucinations in responses generated by large language models (LLMs). RelD is trained using a newly constructed dataset, RelQA, which features bilingual question-answering dialogues and metrics designed to evaluate the faithfulness and consistency of LLM outputs.
     - **Details of RelD Framework**:
       - Trained on RelQA, a dataset that includes:
         - Diverse questions and responses from LLMs.
         - Annotated hallucinations using a comprehensive set of evaluation metrics.
       - Capable of detecting hallucinations across multiple LLMs and datasets.
       - Types of Hallucinations Analyzed: Faithfulness Issues & Inconsistencies
   - **Performance**:
     - Effectively identifies hallucinations in both in-distribution (ID) and out-of-distribution (OOD) datasets.
     - Robust against variations in language, task settings, and dialogue complexities.

8. [Fine-Grained Hallucination Detection and Editing for LLMs](https://arxiv.org/pdf/2401.06855) (Aug 2024) [GitHub](https://fine-grained-hallucination.github.io/)
   - **Context**: Addresses the challenge of fine-grained hallucination detection in LLMs, introducing a taxonomy of hallucinations and a benchmark, FavaBench. It also proposes FAVA, a retrieval-augmented model, to detect and edit hallucinated outputs.
     - **Details**: Hallucinations manifest in various forms, including:
       - Factual Errors: Incorrect facts.
       - Logical Inconsistencies: Contradictory or implausible statements.
       - Context Mismatches: Divergence from the input context or task.
   - **Performance**: FAVA outperformed ChatGPT and GPT-4 on FavaBench in both detection and correction.
    
9. [Leveraging Graph Structures to Detect Hallucinations in LLMs](https://arxiv.org/pdf/2407.04485) [GitHub] (Jul 2024) (https://github.com/noanonkes/Hallucination-Detection-in-LLMs)
   - **Context**: Uses Graph Attention Networks (GATs) to identify and differentiate hallucinated from non-hallucinated generations based on their positions and relationships within the latent embedding space.
   - **Key Findings**:
     - Latent Space Structure:
       - Hallucinated and non-hallucinated outputs form discernible structures in the latent space.
       - Embeddings of hallucinated generations are separable from reliable outputs, allowing for graph-based detection.
     - Graph Attention Networks (GATs):
        - A graph-based framework where:
          - Nodes represent outputs (generations).
          - Edges connect nodes that are closely related in the latent space.
        - GATs aggregate information through message passing, assigning weights to neighbors based on relevance, enabling precise hallucination detection.
   - **Performance**:
     - Achieves results comparable to evidence-based benchmarks without relying on external search or retrieval methods.
     - Demonstrates strong generalization to unseen data, outperforming traditional approaches in scalability and efficiency.
   - **Notes**: This approach is a network that requires implementation but can be applied to ChatGPT-generated text by:
       - Generating embeddings of the outputs.
       - Constructing a graph structure based on those embeddings.
       - Using a pre-trained or custom-trained GAT to detect hallucinations.


---

## Important resources

[Calibrated Language Models Must Hallucinate](https://dl.acm.org/doi/pdf/10.1145/3618260.3649777?casa_token=L8p0VzgusuYAAAAA:nwr88f3K4WCdgDYjrygjS8J4ueu-5QRtlBF2sTn04YQNe69VbKmniSk_6zmoyWUnYoNts978GBqK6g)
   - **Take-Aways**:
     - Why Hallucinations Are Inherent:
       - Arbitrary Facts: Hallucinations occur more frequently for facts that are rare or arbitrary (e.g., unique events or names) because their veracity cannot be determined from the training data.
       - Calibration Trade-Off: To maintain accurate confidence levels in predictions, calibrated LLMs may hallucinate, especially for facts that appear only once in the training data.
     - Hallucination Lower Bound:
        - The rate of hallucination for arbitrary facts is tied to the Good-Turing estimate (fraction of facts appearing exactly once in the training data).
        - Even under ideal conditions (perfect data, no errors), hallucinations are inevitable for facts not sufficiently represented in the training corpus.
      - Different Types of Facts:
         - Systematic Facts: Facts governed by rules (e.g., arithmetic) are less prone to hallucination because they can be learned systematically.
         - Arbitrary Facts: Facts like references to publications or specific events are prone to hallucination because they cannot be inferred from patterns in training data.
       - Impact of Model Calibration:
          - A well-calibrated model predicts outputs with probabilities that reflect true likelihoods but does not necessarily minimize hallucinations.
          - Post-training alignment techniques reduce hallucination rates but can harm calibration accuracy.
