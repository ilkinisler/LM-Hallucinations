# LM Hallucination Detection 🧠

A curated list of resources, papers, and tools related to **Language Model (LM)  Hallucination Detection Methods**.

---

## Overview

### Problem Statement
Language models (LMs) frequently produce outputs that are syntactically convincing but factually incorrect or ungrounded in reliable sources. This phenomenon, referred to as hallucination, presents significant challenges in ensuring the reliability, trustworthiness, and practical adoption of AI systems in critical areas such as healthcare, education, and policy-making. The focus is on tracking AI-generated outputs, evaluating their groundedness, and ensuring their faithfulness to reliable sources to distinguish between real data and synthetic outputs.

### Key Terms
- **Hallucination**: Outputs generated by a language model that are factually inaccurate or ungrounded in training data or real-world knowledge.
- **Groundedness**: The extent to which an AI's outputs can be traced back to reliable and credible sources.
- **Faithfulness**: The alignment between generated content and the source data it is derived from.
- **Synthetic Language Data**: Text created by AI models rather than written by humans.
- **Traceability**: The ability to track the origin of an AI-generated text and verify its authenticity.

---

## Challenges
- **Defining and Quantifying Hallucination**:
  - Challenge: Lack of universally accepted definitions and metrics for hallucination leads to inconsistencies in evaluation and comparison of methods. Hallucinations can range from factual inaccuracies to logical inconsistencies or irrelevance to the prompt.
  - Impact: This ambiguity complicates both detection methods and the development of benchmarks.

- **Dependence on External Knowledge Sources**:
  - Challenge: Many hallucination detection methods rely on external knowledge bases or retrieval systems for fact-checking. These sources may be incomplete, outdated, or biased.
  - Impact: The quality of hallucination detection is often limited by the reliability and comprehensiveness of these external resources.

- **Semantic and Contextual Ambiguity**:
  - Challenge: Determining factuality requires understanding the semantic and contextual nuances of the generated text. Even seemingly correct statements might lack proper context or contradict implicit assumptions.
  - Impact: Detection tools must go beyond surface-level analysis to account for deeper semantic relationships.
 
- **Lack of Ground Truth**:
  - Challenge: Establishing a ground truth for every generated statement is difficult, especially in open-domain text generation where outputs are diverse and unpredictable.
  - Impact: Without reliable ground truth data, training and evaluating hallucination detection systems becomes challenging.

- **Differentiating Hallucinations from Errors**:
  - Challenge: Some outputs may result from poor reasoning or training data errors, rather than outright hallucination. Separating these issues requires sophisticated detection frameworks.
  - Impact: Misclassifying errors as hallucinations (or vice versa) can undermine the effectiveness of detection systems.

- **Generalization Across Domains**:
  - Challenge: Detection systems often struggle to generalize across different domains (e.g., medical vs. legal vs. creative writing) due to variations in factuality standards and text structures.
  - Impact: Domain-specific fine-tuning is costly and may still not achieve complete coverage.

- **Trade-off Between Detection and Model Performance**:
  - Challenge: Efforts to reduce hallucinations often lead to conservative models that avoid generating creative or exploratory responses.
  - Impact: Balancing hallucination detection with maintaining model creativity and informativeness is an ongoing challenge.

- **Real-Time Detection Constraints**:
  - Challenge: Detecting hallucinations in real-time requires efficient algorithms that do not introduce significant computational overhead.
  - Impact: This is especially critical for applications like customer service, where latency impacts user experience.

- **Adversarial Prompts**:
  - Challenge: Hallucinations are more likely to occur when the model is fed adversarial or ambiguous prompts that lead to nonsensical completions.
  - Impact: Robust detection methods must account for the influence of such prompts while maintaining their ability to process legitimate ambiguous queries.

- **Calibration and Confidence Scores**:
  - Challenge: LLMs often overestimate their confidence in hallucinated outputs, making it harder to rely on model-generated confidence scores for detection.
  - Impact: Developing methods to improve calibration without reducing model performance is complex.

- **Evaluation Metrics**:
  - Challenge: There is no standard set of metrics to evaluate hallucination detection systems. Metrics like precision, recall, or F1 score may not fully capture the complexity of hallucinations.
  - Impact: The lack of consistent evaluation frameworks makes it hard to compare different approaches.

- **Ethical and Trust Issues**:
  - Challenge: Hallucination detection directly impacts user trust in AI systems, particularly in high-stakes applications like healthcare or legal advice.
  - Impact: The inability to reliably detect hallucinations can result in ethical and legal consequences.

- **Multi-Language and Cross-Cultural Considerations**:
  - Challenge: Hallucination detection systems often perform poorly in non-English languages or fail to account for cross-cultural variations in factuality and expression.
  - Impact: Building robust systems for diverse linguistic and cultural contexts requires extensive resources.

- **Ambiguity in Low-Resource Data**:
  - Challenge: In low-resource domains or languages, the scarcity of high-quality training data exacerbates the hallucination problem.
  - Impact: This limits the development and evaluation of robust detection systems in these contexts.

- **Detecting Subtle Hallucinations**:
  - Challenge: Some hallucinations are not blatantly incorrect but subtly misleading or unverifiable, making them harder to detect.
  - Impact: Detecting such cases requires sophisticated systems capable of nuanced analysis.

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
    
8. [Fine-Grained Hallucination Detection and Editing for LLMs](https://arxiv.org/pdf/2401.06855) (COLM 2024) [GitHub](https://fine-grained-hallucination.github.io/)
     - FavaBench Benchmark:
       - Includes ~1,000 fine-grained human judgments on outputs from ChatGPT, Llama2-Chat (70B, 7B), and others.
       - Evaluates hallucination detection across multiple domains, focusing on both detection and correction tasks.


---

## Hallucination Detection Methods

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

8. [Fine-Grained Hallucination Detection and Editing for LLMs](https://arxiv.org/pdf/2401.06855) (COLM 2024) [GitHub](https://fine-grained-hallucination.github.io/)
   - **Context**: Addresses the challenge of fine-grained hallucination detection in LLMs, introducing a taxonomy of hallucinations and a benchmark, FavaBench. It also proposes FAVA, a retrieval-augmented model, to detect and edit hallucinated outputs.
     - **Details**: Hallucinations manifest in various forms, including:
       - Factual Errors: Incorrect facts.
       - Logical Inconsistencies: Contradictory or implausible statements.
       - Context Mismatches: Divergence from the input context or task.
   - **Performance**: FAVA outperformed ChatGPT and GPT-4 on FavaBench in both detection and correction.
    
9. [Leveraging Graph Structures to Detect Hallucinations in LLMs](https://arxiv.org/pdf/2407.04485) (Jul 2024) [GitHub](https://github.com/noanonkes/Hallucination-Detection-in-LLMs)
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

## Groundedness Detection Methods

1. [Measuring the Groundedness of Legal Question-Answering Systems](https://arxiv.org/pdf/2410.08764) (Oct 24)
  - **Context**: Focuses on verifying whether AI-generated legal responses are well-grounded in provided documents.
Uses legal question-answering as a test domain due to the importance of accuracy and traceability in high-stakes applications.
  - **How It Works (Applicability)**: Uses similarity-based metrics and natural language inference (NLI) models to check if responses align with source materials.
Evaluates different prompting strategies for large language models (LLMs) to improve detection of ungrounded responses.
  - **Performance**: Achieves a macro-F1 score of 0.8, indicating strong accuracy in detecting grounded responses.
  - **Key Findings**:
    - Found that retrieval-augmented prompting improves groundedness detection.
    - Certain NLI models outperform similarity-based approaches in verifying legal responses.
    - Latencies of different approaches were analyzed to assess real-world applicability.

2. **CaLM**: [Contrasting Large and Small Language Models to Verify Grounded Generation](https://arxiv.org/pdf/2406.05365) (Jun 2024)
  - **Context**: Compares large and small LMs to determine if generated text is verifiably grounded in source material.
Uses a small LM as a reference to validate the output of larger LMs.
  - **How It Works (Applicability)**: Small models (which are less prone to hallucination) cross-check responses generated by larger models.
If a larger LM’s output aligns with a smaller LM that has access only to the cited sources, it is considered grounded.
Discrepancies trigger an iterative feedback loop for refinement.
  - **Performance**: Improves accuracy by 1.5% to 7% across three open-domain QA datasets without requiring model fine-tuning.
  - **Key Findings**:
    - Smaller LMs are more factually consistent than larger models and help validate outputs.
    - Feedback loops improve response groundedness over multiple refinement iterations.
    - Can be used alongside RAG systems to improve factual reliability.

3. [Groundedness in Retrieval-Augmented Long-Form Generation: An Empirical Study](https://arxiv.org/pdf/2404.07060) (Apr 2024)
  - **Context**: Investigates how well retrieval-augmented generation (RAG) models ground their long-form responses.
  - **How It Works (Applicability)**: Analyzes whether each sentence in an AI-generated long-form answer is explicitly grounded in retrieved documents.
Considers both retrieved sources and model pretraining data.
  - **Performance**: Identified that many generated responses contain factual answers but lack explicit grounding in sources.
  - **Key Findings**:
    - Even correct responses often lack explicit grounding in the provided retrievals.
    - Larger models improve grounding slightly but still hallucinate information.
    - Instruction tuning improves grounding but does not fully resolve the issue.

4. [How Well Do Large Language Models Truly Ground?](https://arxiv.org/pdf/2311.09069)
  - **Context**: Challenges the common definition of grounding (just having a correct answer). Proposes a stricter definition:
    - The response must fully use the provided knowledge.
    - The response must stay within the given knowledge limits.
  - **How It Works (Applicability)**: Introduces a new dataset and a grounding metric to evaluate models. Tests grounding capabilities across 25 LLMs of different sizes.
  - **Performance**: Shows that most LLMs fail to fully ground their responses, even when retrieving the correct documents.
  - **Key Findings**:
    - LLMs frequently generate ungrounded information, even if they cite sources.
    - Larger models slightly improve grounding but still introduce hallucinations.
    - Newer instruction-tuned models perform better in grounding tasks.

5. [Effective Large Language Model Adaptation for Improved Grounding and Citation Generation](https://arxiv.org/pdf/2311.09533)
  - **Context**: Addresses the issue of hallucinated citations in LLMs. Introduces AGREE, a framework for improving grounding and citation generation.
  - **How It Works (Applicability)**: Fine-tunes LLMs to ensure self-grounded claims. Uses retrieved passages to verify citation accuracy. Introduces test-time adaptation (TTA) where models actively retrieve missing evidence during response generation.
  - **Performance**: Outperforms prompting-based and post-hoc citation approaches across five datasets.
  - **Key Findings**:
    - Retrieval-based tuning significantly improves citation accuracy.
    - Test-time adaptation allows LLMs to actively correct ungrounded claims.
    - Reduces hallucinated references compared to traditional citation models.

---

## Important resources

[Calibrated Language Models Must Hallucinate](https://dl.acm.org/doi/pdf/10.1145/3618260.3649777?casa_token=L8p0VzgusuYAAAAA:nwr88f3K4WCdgDYjrygjS8J4ueu-5QRtlBF2sTn04YQNe69VbKmniSk_6zmoyWUnYoNts978GBqK6g)
   - **Take-Aways**:
      - Calibrated Models Inevitably Hallucinate:
        - The paper concludes that hallucinations in language models (LLMs) are not merely a result of poor training or inadequate data but are statistically inevitable for calibrated models when dealing with rare or arbitrary facts.
        - This finding emphasizes that even in idealized scenarios (perfect training data, no errors), hallucinations cannot be entirely avoided for certain categories of facts.
      - Good-Turing Estimate and Hallucination Rates:
        - The hallucination rate for arbitrary facts correlates closely with the Good-Turing estimate, which quantifies the fraction of facts that appear only once in the training data.
        - This means that the more sparse or unique the facts in the dataset, the higher the hallucination rates are likely to be, even for well-calibrated models.
      - Role of Calibration:
        - Calibration ensures that a model's predicted probabilities reflect the true likelihood of events, but this statistical accuracy doesn't guarantee factual reliability.
        - There’s a trade-off between reducing hallucinations and maintaining accurate calibration: post-training methods that reduce hallucinations (e.g., reinforcement learning) often compromise calibration quality.
      - Systematic vs. Arbitrary Facts:
        - Models are less prone to hallucinations with systematic facts (e.g., mathematical or rule-based information) because these are learnable from patterns.
        - Arbitrary facts (e.g., unique events or citations) are inherently more challenging since their likelihood cannot be generalized from limited data.
    
