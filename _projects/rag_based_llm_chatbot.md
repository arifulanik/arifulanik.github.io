---
layout: page
title: RAG-Based LLM Chat Bot
description: Desktop PDF question answering with retrieval-augmented generation.
importance: 4
category: research
img: assets/img/RAG_LLM_CHAT.png
---

Built a desktop application that combines Retrieval-Augmented Generation (RAG) with a large language model to answer natural-language questions about user-uploaded PDF documents. Answers are grounded in the document while retaining the model's broader reasoning ability.

![RAG and LLM desktop application]({{ '/assets/img/RAG_LLM_CHAT.png' | relative_url }})

## Workflow

1. A user uploads a PDF in the Tkinter desktop interface.
2. PyMuPDF extracts the document text; LangChain chunks and indexes it for semantic retrieval.
3. For each question, the application retrieves the most relevant passages and supplies them with the question to the LLM.
4. The interface presents the answer and provides a Clear action to reset the question and answer fields.

## Technical challenges and impact

- Balanced chunk quality and retrieved-context size to keep answers relevant without exceeding model context limits.
- Handled varied PDF structures and layouts through robust text extraction.
- Kept the GUI responsive while parsing, retrieval, and generation run in the background.

The result is a lightweight, self-contained tool that helps users find answers in PDFs without manually searching every page.

**Tech:** Python, LangChain, PyMuPDF, Tkinter, LLM-based RAG.
