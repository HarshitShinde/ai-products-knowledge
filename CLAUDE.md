# ai-products-knowledge — context

Personal knowledge base for Harshit Shinde's **MIT xPRO "AI Product Management"**
cohort course, plus one unrelated capstone-style product design doc. This file
orients any future session working in this repo.

## Repo layout

```
Introduction/            Pre-course orientation webinars (all cohorts/leaders)
Module_1/                Introduction to the AI Design Process
Module_2/                AI Technology Fundamentals: Machine Learning
Module_3/                AI Technology Fundamentals: Deep Learning
Module_4/                Designing Artificial Machines to Solve Problems
project_details.md       Unrelated: iMatchX product design doc (AI Design
                          Process case study for a 3-way match exception
                          triage product), owned separately from the course
                          material above.
```

Each `Module_N/` generally contains:
- `Module N_Quick Reference Guide.pdf` — condensed summary of learning outcomes and concepts for that module.
- `Module N_Video Transcripts.pdf` — transcripts of the recorded lecture videos.
- `Mini-Lessons/` (Modules 2–3) or `Mini-Lession_N.1.docx` (Module 4) — supplementary short lessons, .docx.
- `Assignments/` (Module 1) — case studies, workbooks, activities (.pdf/.docx/.pptx/.xlsx).
- `Live Sessions/` or `Live_Sessions/` (naming is inconsistent across modules — Module 3 uses an underscore, the others use a space) — recordings/materials from weekly live office hours and webinars:
  - `*TRANSCRIPT.txt` — WEBVTT-format transcripts of Zoom office-hour recordings, one per facilitator (Bruce Lam, Danny Malter, Dr. Amanda Fetch are the recurring program leaders/facilitators).
  - Facilitator slide decks / cheat sheets (.pdf).
  - Occasional extras, e.g. `Module_2/Live Sessions/executive_ml_wizard.html`.

`Introduction/` mirrors the `Live Sessions/` pattern (per-facilitator webinar transcripts + slide PDFs) but covers the pre-course orientation rather than a specific module.

## Module content summary

- **Module 1 — Introduction to the AI Design Process**: the 4-stage AI Design Process (Intelligence → Business Process → AI Technology → Tinkering), the AI ecosystem (ML/DL/CV/NLP/LLMs/RAG/multimodal/agents), the Delta model's three competitive strategies, and "AI cancers" (adversarial attacks, lack of generalization, bias, explainability, unintended behavior).
- **Module 2 — Machine Learning fundamentals**: supervised/unsupervised/semi-supervised learning, parametric vs. non-parametric models, linear classifiers, decision trees, bagging/random forests/boosting, Bayesian methods, regression (linear/logistic/SVM, gradient descent), k-means and hierarchical clustering.
- **Module 3 — Deep Learning fundamentals**: neural network components (MLPs, weights, activation functions, gradient descent/backprop), CNNs, RNNs/LSTMs/GRUs, autoencoders, and a case study on AI-assisted breast cancer screening (MIT's Tempo project).
- **Module 4 — Designing Artificial Machines to Solve Problems**: an end-to-end worked case study applying the 4-stage AI Design Process to a voice-based diagnostic product (Alzheimer's/COVID), covering ResNets and the "Open-Voice Brain Model Architecture" (OVBM), dataset augmentation via biomarkers, IRB/consent approval for human experimentation, and the pros/cons of MTurk-based crowdsourcing.

## Working with this content

- Transcript `.txt` files are large, verbatim WEBVTT captions (timestamps + speaker names) from live Zoom sessions — treat them as raw source material, not summaries.
- `.pdf` quick-reference guides are the best single-file summary of each module's material if you need a fast overview.
- `.docx`/`.pptx`/`.xlsx` files require the docx/pptx/xlsx skills to read or edit, not the plain `Read` tool.
- `project_details.md` is a separate, self-contained product design document (iMatchX) — unrelated to the course modules; don't conflate the two when asked to "update the course" or similar.
