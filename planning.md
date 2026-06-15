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
Chunk size: 200 tokens

**Overlap:**
Overlap size: 50 tokens (about 1–2 sentences)

**Reasoning:**
The documents vary from primarly short paragraphs to a few longers ones, so 200 tokens sits in the middle of that range 

200 tokens translates to roughly 2 paragraphs

Overlap size of 50 tokens retains about a sentence or two of context, which will be helpful for the longer chunks
---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model:**
Using recommended model - all-MiniLM-L6-v2 via sentence-transformers

**Top-k:**
Using top 3 chunks - don't need too much context to pull info on one professor

**Production tradeoff reflection:**

I would wwitch to a more advanced model for more specificity/accuracy.

I would also increase top k to around 5 for more context and higher accuracy, but this would also require more documents/information to retrive from, as there's no point in getting more context unless the context is diverse enough. 

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 | What do students say about Prof. Jayanti's teaching style and course difficulty? | Students describe Jayanti as clear and organized, with challenging but fair exams. Reviews mention the course is rigorous but rewarding for those who put in effort. |
| 2 | How does Prof. Kommeneni compare to other CS professors at Dartmouth in terms of helpfulness and accessibility? | Kommeneni is noted as approachable and responsive to student questions during office hours. Students appreciate her willingness to help and explain concepts multiple times. |
| 3 | What programming languages or topics does Prof. Tregubov typically teach, and what is the workload like in his courses? | Tregubov teaches courses covering systems/lower-level programming. Students report moderate to heavy workload with significant programming projects and problem sets. |
| 4 | Which CS professors are recommended for beginners or students new to computer science? | Multiple sources recommend professors who explain fundamentals clearly and are patient with struggling students. Look for reviews emphasizing approachability and clear explanations. |
| 5 | What are students' main criticisms or complaints about CS courses at Dartmouth? | Common themes include heavy workload, rushed pacing in some courses, and occasionally unclear grading rubrics. Some students note the workload increases significantly in upper-level courses. |

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->
 
1. The information comes from very different time periods. Some of the professors don't teach there anymore, some teach different classes, and the curriculums of courses have likely changed over time. A good way to fix this would be to have a source that documents what classes currently exist, who is teaching them, and then cross-reference this with the sources I provided. If the mentioned professor doesn't teach anymore, then that information should not be returned to the user.


2. Reviews and experiences across students might be too varied to provide an accurate potrayal of a professor and their class. Even if the model works exactly as intended, it might not be very useful. A way to improve on this might be including more statistically backed information, like grades or number of hours spent on homework.

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->


  ┌──────────────────┐      ┌──────────────────┐      ┌──────────────────┐
  │   INGESTION      │      │    CHUNKING      │      │   EMBEDDING      │
  │                  │      │                  │      │                  │
  │ • LayupList      │      │ • 200 tokens     │      │ • sentence-      │
  │ • Reddit posts   │─────→│ • 50-token       │─────→│   transformers   │
  │ • Quora Q&A      │      │   overlap        │      │ • all-MiniLM-    │
  │ • Articles       │      │ • Semantic       │      │   L6-v2          │
  │                  │      │   boundaries     │      │                  │
  └──────────────────┘      └──────────────────┘      └──────────────────┘
                                                                │
                                                                │
                                                                ↓
                                                      ┌──────────────────┐
                                                      │  VECTOR STORE    │
                                                      │                  │
                                                      │ • ChromaDB       │
                                                      └──────────────────┘
                                                                │
         ┌──────────────────┐                                   │
         │  USER QUERY      │                                   │
         └────────┬─────────┘                                   │
                  │                                             │
                  │            ┌──────────────────┐             │
                  ├───────────→│   RETRIEVAL      │←────────────┤
                  │            │                  │
                  │            │ • Dense search   │
                  │            │ • Top-k = 3      │
                  │            │ • Similarity     │
                  │            └────────┬─────────┘
                  │                     │
                  │         ┌───────────┴───────────┐
                  │         │ (Top 3 chunks)        │
                  │         └───────────┬───────────┘
                  │                     │
         [GROQ API]                     │
          ┌─────────────────────────────┘
          │
          ↓
  ┌──────────────────┐
  │   GENERATION     │
  │                  │
  │ • Groq API       │
  │ • llama-3.3-     │
  │   70b-versatile  │
  └────────┬─────────┘
           │
           ↓
    ┌────────────────┐
    │  ANSWER        │
    │ with sources   │
    └────────────────┘


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
