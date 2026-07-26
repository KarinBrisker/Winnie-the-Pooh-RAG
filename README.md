# Winnie-the-Pooh RAG

A compact Retrieval-Augmented Generation experiment built around the text of *Winnie-the-Pooh*. The repository demonstrates the core stages of a RAG pipeline: document preparation, chunking, embedding, retrieval, prompt construction, generation, and qualitative evaluation.

## Purpose

The project is intended as an inspectable learning artifact for understanding how retrieved evidence can improve language-model responses over a bounded corpus.

Rather than treating RAG as a single model call, the notebook exposes the individual system components and the assumptions behind them.

## Pipeline

```text
Source text
   ↓
Cleaning and chunking
   ↓
Embedding generation
   ↓
Vector index
   ↓
Query retrieval
   ↓
Context assembly
   ↓
Grounded answer generation
```

## What the notebook covers

- Loading and preprocessing a source corpus
- Splitting text into retrievable chunks
- Producing vector representations
- Building a similarity-search index
- Retrieving context for a user query
- Passing retrieved evidence to a generative model
- Inspecting answers and retrieval quality

## Repository contents

- `Winnie_the_Pooh_RAG_task.ipynb` — end-to-end experiment and explanation

## Requirements

- Python 3.8+
- Jupyter Notebook or JupyterLab
- `transformers`
- `torch`
- `datasets`
- `faiss-cpu`

## Setup

```bash
git clone https://github.com/KarinBrisker/Winnie-the-Pooh-RAG.git
cd Winnie-the-Pooh-RAG
pip install transformers torch datasets faiss-cpu
jupyter notebook
```

Open `Winnie_the_Pooh_RAG_task.ipynb` and run the notebook cells in order.

## Design questions explored

- How should a narrative corpus be split into useful retrieval units?
- What information is lost when chunks are too short or too long?
- Does the retriever return evidence that actually supports the generated answer?
- How should the system behave when the corpus does not contain the answer?
- How much of answer quality comes from retrieval versus generation?

## Evaluation perspective

This repository currently emphasizes qualitative inspection. A stronger evaluation layer could add:

- retrieval recall over a labeled question set,
- answer groundedness,
- citation or evidence correctness,
- answerable versus unanswerable query behavior,
- comparison of chunking strategies,
- dense retrieval versus hybrid retrieval,
- reranking ablations.

## Limitations

- The corpus is small and domain-bounded.
- Results are sensitive to chunking, embedding choice, and model configuration.
- Similarity does not guarantee that retrieved text supports the answer.
- The notebook is an experiment, not a production-ready RAG service.

## Why it matters

The useful lesson in a small RAG project is not only that retrieval can improve generation. It is that retrieval quality, context construction, and evaluation are separate engineering problems that must be measured independently in real systems.

## Contributing

Suggestions that improve the experiment, evaluation methodology, or reproducibility are welcome.

## License

This project is licensed under the MIT License.
