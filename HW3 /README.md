# CS235 Homework 3 — Text Classification

This assignment investigates the impact of different text representation techniques on multi-class news article classification using the New York Times (NYT) dataset. Each article consists of raw text and an associated topic label. The primary objective is to compare classical and modern NLP feature representations under a consistent classification framework and evaluate their effectiveness using standard performance metrics.

The dataset is first shuffled using a fixed random seed (42) to ensure reproducibility and then split into training (80%), validation (10%), and test (10%) sets. Across all experiments, logistic regression is used as the classifier, except for the BERT model, which is fine-tuned end-to-end. Performance is evaluated on the test set using accuracy, macro-F1, and micro-F1 scores, where macro-F1 emphasizes per-class balance and micro-F1 reflects overall classification effectiveness.

## Bag of Words:
The first set of experiments focuses on Bag-of-Words (BoW) representations. Three variants are explored: (i) binary presence vectors indicating whether a word appears in a document, (ii) raw term-frequency vectors capturing word counts, and (iii) TF-IDF vectors that down-weight common terms while emphasizing discriminative words. These approaches provide a baseline for understanding how increasingly informative lexical features affect classification performance.

## Word2Vec
The second group of experiments evaluates distributed word representations using 100-dimensional embeddings. In the first approach, pre-trained GloVe embeddings are used, and each document is represented as the average of its constituent word vectors. In the second approach, Word2Vec embeddings are trained directly on the NYT corpus, and document vectors are similarly constructed via averaging. These experiments examine whether semantic representations learned from large corpora or task-specific data improve classification compared to sparse BoW features.

## BERT
The final experiment involves fine-tuning BERT (bert-base-uncased) for text classification. Articles are tokenized with a maximum sequence length of 64 tokens, and the model is fine-tuned for three epochs using the Hugging Face Transformers library. Unlike previous methods, BERT jointly learns contextual representations and the classifier, enabling it to capture deeper syntactic and semantic relationships within the text.

## Conclusion
The assignment concludes with a comparative analysis of all methods, discussing performance trends, strengths, and limitations of each representation. Overall, the homework provides a systematic comparison between traditional vector space models, word-embedding–based approaches, and transformer-based models for real-world text classification tasks, highlighting the trade-offs between simplicity, interpretability, and predictive performance
