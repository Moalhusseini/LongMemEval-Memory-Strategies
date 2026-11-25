# LongMemEval: Memory-Management Strategies

An exploratory comparison of memory-management strategies for long-term conversational memory in large language models, using the **LongMemEval-S Cleaned** benchmark.

## Research Question

Which memory-management strategy provides the best balance between answer accuracy, evidence recall, token usage, and response latency in long conversations?

## Methods

Four strategies were evaluated:

- **Full Context** — the complete conversation history
- **Trimming** — the most recent complete sessions
- **Vector-Based RAG** — sessions retrieved using embeddings and cosine similarity
- **Importance Scoring** — sessions ranked by recency, information density, and personal relevance

Memory budgets for limited-memory strategies:

| Budget | Tokens |
|---|---:|
| Low | 16,384 |
| High | 65,536 |

The experiment used six questions—one from each question type—covering **301 sessions and 3,019 turns**. The sample was selected using fixed random seeds.

## Main Results

- **RAG (High)** achieved the highest answer accuracy: **66.67% (4/6)** and macro evidence recall of **1.0000**.
- **RAG (Low)** achieved the highest macro evidence F1: **0.2615**.
- **Importance Scoring (Low)** had the shortest mean answer-generation latency: **0.70 seconds**.

These findings are preliminary. The sample contains only six questions, so results should not be interpreted as statistically generalizable or as a definitive ranking.

## Repository Contents

- `LongMemEval_Memory_Strategies_Research.ipynb` — experimental notebook
- `Research_Report.pdf` — research report with references

## Reproducibility Notes

The notebook documents the experiment and its evaluation. The dataset is not included in this repository; obtain it from the official LongMemEval source and place the cleaned JSON file at the path expected by the notebook.

The report notes limitations including the small sample, manual binary answer labels, and differences in generation settings across some API calls. API credentials should be supplied through environment variables and never committed.

## References

See the references section in [`Research_Report.pdf`](Research_Report.pdf).
