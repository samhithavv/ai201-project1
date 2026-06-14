# Project 1 Planning: The Unofficial Guide

> Write this document before you write any pipeline code.
> Your spec and architecture diagram are what you'll use to direct AI tools (Claude, Copilot, etc.) to generate your implementation — the more specific they are, the more useful the generated code will be.
> Update the Retrieval Approach and Chunking Strategy sections if you change your approach during implementation.
> Update this file before starting any stretch features.

---

## Domain

<!-- What domain did you choose? Why is this knowledge valuable and hard to find through official channels? -->
I chose reviews of CS professors at Dartmouth College, which is my school. I believe this information is valuable because it's tough to find a consolidated source of information across different sources. Students can signficantly improve their academic experiences if they have more information prior to choosing classes (more advice would have definitely helped me).
---

## Documents

<!-- List your specific sources: URLs, subreddit names, forum threads, or file descriptions.
     Aim for at least 10 sources that together cover different subtopics or perspectives within your domain. -->

| # | Source | Description | URL or location |
|---|--------|-------------|-----------------|
| 1 | https://www.layuplist.com/course/690/review_search?q=Prasad%20Jayanti | Review of CS prof (Jayanti) from Dartmouth's unique course review site | No public access, will be made into txt file |
| 2 | https://www.reddit.com/r/dartmouth/comments/i83id6/best_cs_profs/ | Reddit of best CS profs/classes | Publicly available |
| 3 | https://www.layuplist.com/course/680/review_search?q=Vasanta%20Lakshmi%20Kommineni | Review of CS prof (Kommineni) from Dartmouth's unique course review site | No public access, will be made into txt file |
| 4 | https://www.layuplist.com/course/682/review_search?q=Timothy%20Pierson | Review of CS prof (Pierson) from Dartmouth's unique course review site | No public access, will be made into txt file |
| 5 | https://www.reddit.com/r/dartmouth/comments/eq1qe3/best_classes_you_have_taken_at_dartmouth_with/| Best profs/classes at Dartmouth | Publicly available |
| 6 | https://www.reddit.com/r/dartmouth/comments/8szq0u/help_me_out_regarding_cs/ | Advice on CS at Dartmouth | Publicly available |
| 7 | https://www.layuplist.com/course/691/review_search?q=Deeparnab%20Chakrabarty | Review of CS prof (Deep C) from Dartmouth's unique course review site | No public access, will be made into txt file |
| 8 | https://www.layuplist.com/course/3149/review_search?q=Timothy%20Tregubov | Review of CS prof (Tregubov) from Dartmouth's unique course review site | No public access, will be made into txt file |
| 9 | https://www.quora.com/What-are-the-pros-and-cons-of-studying-in-Dartmouth-Colleges-computer-science-program | CS department review | Publicly available |
| 10 | https://dartreview.com/success-in-computing-at-dartmouth/ | Article on the CS department's changes over times | Public |

---

## Chunking Strategy

<!-- How will you split documents into chunks?
     State your chunk size (in tokens or characters), overlap size, and explain why those
     numbers fit the structure of your documents.
     A review-heavy corpus warrants different chunking than a long FAQ. -->

**Chunk size:**

**Overlap:**

**Reasoning:**

---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model:**

**Top-k:**

**Production tradeoff reflection:**

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 | | |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->

1.

2.

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->

---

## AI Tool Plan

<!-- For each part of the pipeline below, describe:
     - Which AI tool you plan to use (Claude, Copilot, ChatGPT, etc.)
     - What you'll give it as input (which sections of this planning.md, which requirements)
     - What you expect it to produce
     - How you'll verify the output matches your spec

     "I'll use AI to help me code" is not a plan.
     "I'll give Claude my Chunking Strategy section and ask it to implement chunk_text()
     with my specified chunk size and overlap" is a plan. -->

**Milestone 3 — Ingestion and chunking:**

**Milestone 4 — Embedding and retrieval:**

**Milestone 5 — Generation and interface:**
