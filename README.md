# StudyMate — NLP-Based Academic Question Answering System

StudyMate is a document-grounded academic question-answering prototype for the Natural Language Processing (NLP) course project. Students upload their own text-selectable course PDFs or TXT notes, ask questions in natural language, and receive relevant excerpts with document and page references.

> **Project scope:** This implementation is an extractive baseline. It retrieves passages from the uploaded material and selects relevant sentences; it does not use an LLM or invent answers.

## Features

- PDF and TXT ingestion with page metadata
- Text cleanup and sentence-based overlapping chunks
- Tokenization, lowercasing, stop-word filtering, and Porter stemming
- TF-IDF representation with unigram and bigram features
- Cosine-similarity passage retrieval and ranking
- Extractive sentence selection
- Source document and page references
- Configurable relevance threshold and no-answer handling
- Question preprocessing and ranked passages visible for demonstration

## Repository structure

```text
NLP-project/
├── app.py
├── requirements.txt
├── StudyMate_NLP_Question_Answering_Demo.ipynb
├── README.md
└── .gitignore
```

## Run locally

Python 3.10+ is recommended.

```bash
python -m venv .venv

# macOS / Linux
source .venv/bin/activate

# Windows PowerShell
# .venv\Scripts\Activate.ps1

pip install -r requirements.txt
python app.py
```

The app launches a Gradio interface and creates a temporary share URL. Upload only documents you are comfortable sharing through that temporary public link.

## Run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `StudyMate_NLP_Question_Answering_Demo.ipynb` from this repository.
3. Run the dependency-installation cell.
4. Run the application cell and open the Gradio URL it prints.
5. Upload your own NLP course notes, select **Build study index**, and then ask a question.

## NLP concepts demonstrated

| Stage | Technique |
|---|---|
| Text preprocessing | Lowercasing, tokenization, stop-word filtering |
| Stemming | Porter Stemmer |
| Text representation | TF-IDF with unigrams and bigrams |
| Information retrieval | Cosine similarity |
| Passage ranking | Similarity-based ranking |
| Answer selection | Extractive sentence ranking |
| Traceability | Source filename and page number |

## Suggested demo questions

Ask questions whose answers are present in the files you upload, for example:

- What is tokenization in NLP?
- Explain the Viterbi algorithm.
- What is the difference between stemming and lemmatization?
- How does TF-IDF represent a document?

Also try a question that is not covered by the uploaded notes to demonstrate the no-answer response.

## Limitations

- Scanned/image-only PDFs are not supported; the PDF must contain selectable text.
- TF-IDF is lexical retrieval and can miss semantically similar paraphrases with little word overlap.
- Similarity scores are ranking signals, not calibrated probabilities or guaranteed answer confidence.
- Answers are extracted from source passages. They are not generated explanations.
- The initial implementation searches only uploaded documents, not the open web.

## Future improvements

- Add semantic retrieval using sentence embeddings and compare it with the TF-IDF baseline.
- Add OCR support for scanned notes.
- Add a small manually labelled evaluation set and report Precision@k / Recall@k.
- Improve answer grouping across multiple pages while preserving citations.

## References

- Manning, C. D., Raghavan, P., & Schütze, H. (2008). *Introduction to Information Retrieval*. Cambridge University Press.
- Robertson, S., & Zaragoza, H. (2009). The Probabilistic Relevance Framework: BM25 and Beyond. *Foundations and Trends in Information Retrieval*, 3(4), 333–389.
- Jurafsky, D., & Martin, J. H. *Speech and Language Processing*. Draft textbook.
- Karpukhin, V., et al. (2020). Dense Passage Retrieval for Open-Domain Question Answering. *EMNLP 2020*.
