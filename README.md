# Robustness of Sentence Embeddings under Negation

This project investigates whether sentence embedding models (e.g., SBERT) can distinguish between **paraphrases** and **negation-based sentence pairs**, especially when sentences are lexically similar but semantically different.

---

## 📌 Motivation

Sentence embeddings are widely used in:
- Semantic search
- Clustering
- Question answering
- Dialogue systems

These applications assume that **similar embeddings correspond to similar meanings**.

However, this assumption can fail in cases like:

> "It was a fantastic movie."  
> "It was a terrible movie."

These sentences are lexically similar but semantically opposite.

If models cannot distinguish such cases, downstream systems may produce incorrect results.

---

## 🎯 Problem

We aim to evaluate:

- Can embedding models distinguish **paraphrases** from **negation-based non-paraphrases**?
- Do models rely on **semantic understanding** or **surface-level cues**?

---

## 🧩 Dataset

We construct a dataset with two types of sentence pairs:

### 1. Paraphrase pairs (label = 1)
- Source: Microsoft Research Paraphrase Corpus (MRPC)

### 2. Negation-based pairs (label = 0)
- **Explicit negation**  
  e.g., adding "not"
- **Implicit negation**  
  e.g., antonyms, "fail to", semantic reversal

We specifically include **implicit negation**, which is harder and more realistic.

---

## ⚙️ Methods

We compare several approaches:

### Baselines
- TF-IDF + cosine similarity

### Models
- **SBERT + Logistic Regression**
- **Contrastive Fine-tuned SBERT + Logistic Regression**

Contrastive learning is used to:
- Pull paraphrases closer
- Push negation-based pairs apart

---

## 📊 Results

| Method | Accuracy | F1 |
|------|--------|----|
| TF-IDF cosine | ~0.48 | ~0.65 |
| SBERT + Logistic | ~0.92 | ~0.92 |
| Contrastive SBERT | ~0.94 | ~0.94 |

### 🔍 Key Finding

- Implicit negation is **very difficult** for base models  
- Contrastive fine-tuning improves it dramatically:

| Model | Implicit Negation Accuracy |
|------|---------------------------|
| Base SBERT | ~0.32 |
| Contrastive SBERT | ~0.87 |

---

## 🧠 Insights

- High accuracy **does not mean true understanding**
- Base models rely on **shortcut features** (e.g., "not")
- Contrastive learning improves robustness
- But it **reshapes embedding space**, making cosine similarity less interpretable

---

## 🚀 How to Run

### 1. Install dependencies

```bash
pip install sentence-transformers scikit-learn pandas numpy
```

### 2. Run Environments

```bash
jupyter notebook semantic_robustness_evaluation.ipynb
```

---

## 💭 Future Work

- Expand implicit negation dataset
- Balance different negation types
- Explore training methods that preserve semantic similarity
- Compare with cross-encoder models