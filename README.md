Exactly. We should **not** spend equal time on every AI topic.

The curriculum should follow a **0 → 1 → production → advanced → monster** progression, with the **highest-frequency 20% first**. The first ~20% of the curriculum should give you the skills you'll repeatedly use in roughly 80% of real AI application work.

# AI Application Engineering — 0 → MONSTER

## The Learning Strategy

Think of the course as:

```text
                    MONSTER
                       ▲
                       │
              Advanced AI Systems
                       │
              Agents / LangGraph
                       │
                Production RAG
                       │
              LangChain / Tools
                       │
            Structured AI + Streaming
                       │
              LLM Fundamentals
                       │
              TypeScript / Node
                       │
                     0
```

But **time allocation will be uneven**:

```text
┌─────────────────────────────────────────────┐
│ FIRST 20%                                   │
│                                             │
│ LLM APIs                                    │
│ Messages                                    │
│ Prompting                                   │
│ Zod / Structured Output                     │
│ Tool Calling                                │
│ Streaming                                   │
│ Basic RAG                                   │
│ Embeddings                                  │
│ LangChain fundamentals                      │
│ Vercel AI SDK                               │
│                                             │
│ >>> MOST PRACTICAL WORK HAPPENS HERE <<<    │
└─────────────────────────────────────────────┘

                ↓

Remaining 80%

Advanced RAG
LangGraph
Agents
Memory
Multi-agent
Custom adapters
Multimodal
Evaluation
Observability
Security
Cloud
Scaling
Advanced architectures
```

---

# LEVEL 0 — Prerequisites

We won't spend months here because you already work with JavaScript/TypeScript.

## 0.1 Modern TypeScript Required for AI

Only the parts that matter:

* `type`
* `interface`
* generics
* unions
* discriminated unions
* `unknown`
* `Record`
* async/await
* promises
* `AbortController`
* error handling
* modules
* environment variables
* HTTP APIs
* JSON
* streams
* basic functional patterns

### Goal

You should be comfortable writing:

```ts
async function generateAnswer(
  input: GenerateInput
): Promise<GenerateResult> {
  // ...
}
```

Not becoming a TypeScript language-theory expert.

---

# LEVEL 1 — THE 20% THAT MATTERS MOST

This is our **highest-priority section**.

We will go deep here.

---

# Module 1 — What an AI Application Actually Is

Start from:

```text
User
 ↓
Frontend
 ↓
Backend
 ↓
AI Model
 ↓
Response
```

Then understand:

```text
User
 ↓
Validation
 ↓
Authentication
 ↓
Authorization
 ↓
Prompt / Context
 ↓
Model
 ↓
Tools / Retrieval
 ↓
Validation
 ↓
Response
```

Learn:

* AI application architecture
* deterministic vs probabilistic code
* LLM boundary
* backend boundary
* model boundary
* why LLMs should not control your business logic
* request lifecycle
* failure boundaries

### Hands-On

Design an AI coding assistant architecture.

---

# Module 2 — Calling an LLM

Start with the raw SDK.

```text
Node.js
   ↓
Provider SDK
   ↓
LLM
   ↓
Response
```

Learn:

* API keys
* model selection
* request
* response
* messages
* system/user/assistant roles
* async calls
* errors
* timeout
* retries
* token usage
* model configuration

Then:

```text
Raw SDK
   ↓
Reusable AI service
```

### Hands-On

Build:

```text
src/ai/llm.ts
```

with a clean typed interface.

---

# Module 3 — Messages, Tokens & Context

This is foundational.

Learn:

* system messages
* user messages
* assistant messages
* tool messages
* conversation history
* tokenization
* input tokens
* output tokens
* context window
* token limits
* context explosion
* cost implications
* truncation
* summarization

You'll understand exactly what happens when:

```text
User sends message
        ↓
Backend constructs messages
        ↓
Model receives context
        ↓
Model generates tokens
        ↓
Application receives output
```

### Hands-On

Build a conversation manager that controls context size.

---

# Module 4 — Prompt Engineering

Not "100 prompt tricks."

Actual engineering.

Learn:

```text
System Instructions
+
Context
+
User Input
+
Output Contract
```

Topics:

* system prompts
* dynamic prompts
* few-shot examples
* delimiters
* instruction hierarchy
* prompt injection
* prompt versioning
* reusable templates
* prompt testing
* context placement
* when prompting is insufficient

### Hands-On

Create a production prompt library.

---

# Module 5 — Zod + Structured Output

This is one of the **highest-value skills**.

Instead of:

```text
LLM → random text
```

we want:

```text
LLM
 ↓
Structured output
 ↓
Zod
 ↓
Trusted TypeScript object
```

Learn:

* Zod schemas
* schema inference
* enums
* nested objects
* arrays
* optional/nullable
* `parse`
* `safeParse`
* validation failures
* structured generation
* retries
* schema evolution

Example:

```ts
const ReviewSchema = z.object({
  score: z.number().min(0).max(10),
  issues: z.array(z.string()),
  suggestions: z.array(z.string()),
});
```

### Hands-On

Build a typed AI code-review service.

---

# Module 6 — Streaming

Very important for real AI UX.

Learn:

```text
Non-streaming:

Request
   ↓
WAIT
   ↓
Complete response


Streaming:

Request
   ↓
Token
Token
Token
Token
...
```

Learn:

* streaming fundamentals
* async iterators
* server streaming
* cancellation
* abort
* connection errors
* frontend streaming
* partial responses

### Hands-On

Build a streaming AI chat API.

---

# Module 7 — Tool Calling

This is another **80/20 core skill**.

Learn:

```text
User
 ↓
LLM
 ↓
Tool decision
 ↓
Tool call
 ↓
Backend
 ↓
Tool result
 ↓
LLM
 ↓
Final answer
```

Tools:

```text
getUser()
searchProducts()
getWeather()
queryDatabase()
createTicket()
```

Learn:

* tool schemas
* tool descriptions
* arguments
* execution
* validation
* authorization
* errors
* retries
* timeouts
* parallel tools
* tool loops
* dangerous tools
* human approval

### Hands-On

Build an AI assistant with 3 backend tools.

---

# Module 8 — RAG Fundamentals

This is another massive production use case.

Learn:

```text
Documents
 ↓
Chunks
 ↓
Embeddings
 ↓
Vector DB
```

Then:

```text
Question
 ↓
Embedding
 ↓
Similarity Search
 ↓
Relevant Documents
 ↓
Prompt
 ↓
LLM
```

Understand:

* why RAG exists
* hallucination
* grounding
* embeddings
* vector search
* chunking
* metadata
* retrieval
* context injection

### Hands-On

Build your first local RAG application.

---

# Module 9 — Embeddings

Learn only the practical concepts:

* embeddings
* vector representation
* similarity
* cosine similarity
* dimensions
* metadata
* embedding model consistency
* storage
* query embedding

You do **not** need deep mathematical derivations.

### Hands-On

Build semantic search.

---

# Module 10 — ChromaDB

For rapid local development.

Learn:

* collections
* documents
* embeddings
* metadata
* insert
* update
* delete
* similarity search
* filtering
* persistence

### Hands-On

Build:

```text
Document
 ↓
ChromaDB
 ↓
Retriever
 ↓
LLM
```

---

# Module 11 — LangChain.js Fundamentals

Only after understanding the raw architecture.

Learn:

```text
Model
Prompt
Runnable
Tool
Retriever
Output Parser
```

Understand:

* why LangChain exists
* abstractions
* composition
* `invoke`
* `stream`
* `batch`
* model abstraction
* tool abstraction
* retriever abstraction

### Hands-On

Convert your raw AI application into LangChain.

---

# Module 12 — Vercel AI SDK

Now connect the frontend.

Learn:

```text
Next.js
 ↓
Vercel AI SDK
 ↓
AI Backend
 ↓
LLM
```

Topics:

* streaming
* chat state
* messages
* UI integration
* server-side AI
* tool results
* errors
* cancellation
* regeneration

### Hands-On

Build a production-style AI chat UI.

---

# 🚨 END OF THE HIGH-VALUE 20%

At this point you should already be able to build approximately:

```text
              AI APPLICATION
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
       RAG        Tools       Chat
        │           │           │
        └───────────┼───────────┘
                    ▼
                   LLM
                    │
                 Zod
                    │
                Streaming
```

This is the point where you'll have the **core AI application engineering skillset**.

Now we expand toward advanced engineering.

---

# LEVEL 2 — PRODUCTION RAG

## Module 13 — PostgreSQL + pgvector

Move from:

```text
ChromaDB
```

to:

```text
PostgreSQL
+
pgvector
```

Learn:

* schema design
* vector columns
* similarity queries
* HNSW
* metadata filtering
* relational + vector queries
* indexes
* migrations
* connection pooling
* transactions

### Hands-On

Migrate your Chroma RAG application to PostgreSQL.

---

# Module 14 — Production Document Pipeline

```text
Upload
 ↓
Parse
 ↓
Clean
 ↓
Chunk
 ↓
Embed
 ↓
Store
```

Learn:

* PDF
* Markdown
* HTML
* metadata
* deduplication
* document versioning
* incremental indexing
* deletion
* re-indexing

---

# Module 15 — Advanced Retrieval

Learn:

* top-K
* thresholds
* metadata filtering
* hybrid search
* query rewriting
* multi-query
* reranking
* contextual compression
* parent-document retrieval

---

# Module 16 — RAG Evaluation

Learn:

* retrieval relevance
* answer relevance
* groundedness
* faithfulness
* golden datasets
* regression tests
* LLM-as-judge
* human evaluation

---

# LEVEL 3 — LANGCHAIN PRODUCTION

## Module 17 — Advanced LangChain

* Runnable pipelines
* parallel execution
* branching
* custom retrievers
* custom tools
* callbacks
* metadata
* tracing
* error handling

---

# Module 18 — Custom LangChain Tools

Critical for APIs without wrappers.

Pattern:

```text
REST API
   ↓
Typed TS Client
   ↓
Zod Validation
   ↓
LangChain Tool
   ↓
LLM
```

We'll build real custom tools.

---

# Module 19 — Custom Model Adapters

```text
Third-party SDK
      ↓
Adapter
      ↓
Standard AI interface
      ↓
Application
```

We'll cover:

* REST APIs
* NPM SDKs
* streaming
* authentication
* errors
* retries
* normalization

---

# Module 20 — Specialized Providers

Including APIs such as:

```text
Sarvam AI
Speech APIs
TTS
STT
Translation APIs
```

The important lesson is not the individual SDK.

It's:

> **How to integrate any AI provider cleanly into your architecture.**

---

# LEVEL 4 — LANGGRAPH

Now we move from pipelines to stateful workflows.

# Module 21 — Why LangGraph

Understand:

```text
Chain
Workflow
Agent
```

and when each is appropriate.

---

# Module 22 — Graph Fundamentals

```text
START
 ↓
Node
 ↓
Node
 ↓
END
```

Learn:

* nodes
* edges
* state
* reducers
* routing
* conditions
* loops

---

# Module 23 — Stateful Agents

```text
State
 ↓
Reason
 ↓
Tool
 ↓
Observation
 ↓
Reason
 ↓
Tool
 ↓
Final
```

Learn:

* agent loops
* termination
* iteration limits
* state updates
* tool execution

---

# Module 24 — Human-in-the-Loop

```text
Agent
 ↓
Action Proposal
 ↓
Human
 ├── Approve
 └── Reject
```

---

# Module 25 — Persistent Agents

* checkpoints
* threads
* resume
* recovery
* durable state
* long-running workflows

---

# LEVEL 5 — MEMORY

## Module 26 — Conversation Memory

Understand the difference:

```text
Conversation History
       ≠
RAG Knowledge
       ≠
User Memory
       ≠
Agent State
```

Then implement:

* short-term memory
* summarization
* context compaction
* long-term memory
* retrieval-based memory

---

# LEVEL 6 — AGENT ENGINEERING

## Module 27 — Agent Patterns

* Router agent
* Tool agent
* Research agent
* RAG agent
* Planner
* Supervisor
* Human-approved agent

---

## Module 28 — Multi-Agent Systems

```text
Supervisor
   │
   ├── Researcher
   ├── Coder
   ├── Reviewer
   └── Writer
```

Learn:

* delegation
* shared state
* communication
* failure
* cost
* when multi-agent is justified

---

# LEVEL 7 — MULTIMODAL

## Module 29 — Vision

* images
* OCR
* document understanding
* structured extraction
* image + text

---

## Module 30 — Audio

```text
Voice
 ↓
STT
 ↓
LLM
 ↓
TTS
 ↓
Voice
```

---

## Module 31 — Video

* frame extraction
* audio extraction
* multimodal processing
* asynchronous pipelines

---

# LEVEL 8 — AI SEARCH

## Module 32 — Search + RAG

* search APIs
* web retrieval
* source extraction
* citations
* freshness
* untrusted web content
* search grounding

---

# LEVEL 9 — PRODUCTION ENGINEERING

Now we make everything **production-grade**.

## Module 33 — Error Handling

* typed errors
* provider errors
* tool errors
* model errors
* database errors
* fallback
* partial failure

---

## Module 34 — Retries & Timeouts

* exponential backoff
* jitter
* retryable errors
* non-retryable errors
* timeout budgets
* cancellation

---

## Module 35 — Rate Limiting

* user limits
* IP limits
* model limits
* token budgets
* quotas
* abuse prevention

---

## Module 36 — Caching

* response cache
* embedding cache
* retrieval cache
* semantic cache
* invalidation

---

# LEVEL 10 — AI SECURITY

## Module 37 — Prompt Injection

```text
Direct Injection
Indirect Injection
RAG Poisoning
Tool Injection
```

---

## Module 38 — Tool Security

* authorization
* least privilege
* read/write separation
* dangerous operations
* confirmation
* audit logs

---

## Module 39 — Data Security

* PII
* secrets
* logging
* redaction
* retention
* access control

---

# LEVEL 11 — OBSERVABILITY

## Module 40 — AI Logging

Track:

```text
request
model
latency
tokens
cost
tools
retrieval
errors
```

---

## Module 41 — AI Tracing

Trace:

```text
Request
 ├── Prompt
 ├── Model
 ├── Retrieval
 ├── Tool
 ├── Database
 └── Response
```

---

# LEVEL 12 — AI EVALUATION

## Module 42 — Evaluation

* golden datasets
* regression
* structured output testing
* tool testing
* RAG evaluation
* agent evaluation
* LLM judges
* human evaluation

---

# LEVEL 13 — AI COST ENGINEERING

## Module 43 — Cost

Understand:

```text
LLM
+
Embedding
+
Database
+
Compute
+
External APIs
```

---

## Module 44 — Optimization

* smaller models
* model routing
* caching
* context reduction
* token budgets
* batch processing
* embedding reuse

---

# LEVEL 14 — GOOGLE CLOUD

## Module 45 — Docker for AI Applications

* production Dockerfile
* multi-stage builds
* environment variables
* secrets
* health checks

---

## Module 46 — Cloud Run

* deployment
* scaling
* concurrency
* CPU/memory
* cold starts
* health checks

---

## Module 47 — Cloud SQL + pgvector

* PostgreSQL production
* pgvector
* migrations
* backups
* connection pooling
* networking
* security

---

# LEVEL 15 — ASYNC AI

## Module 48 — Background Jobs

For:

```text
PDF processing
Embedding
Video
Batch AI
Long-running agents
```

Architecture:

```text
API
 ↓
Queue
 ↓
Worker
 ↓
AI
 ↓
Database
```

---

## Module 49 — Event-Driven AI

* queues
* webhooks
* workers
* retries
* idempotency
* dead-letter queues

---

# LEVEL 16 — MONSTER

Now we combine everything.

## Module 50 — Model Routing

```text
Simple
 ↓
Cheap Model

Complex
 ↓
Powerful Model

Vision
 ↓
Vision Model

Speech
 ↓
Audio Model
```

---

## Module 51 — Provider Abstraction

```text
Application
     ↓
AI Interface
     ↓
┌────┼────┐
│    │    │
A    B    C
```

Switch providers without rewriting application logic.

---

## Module 52 — AI Gateway

Build a centralized AI gateway responsible for:

* model selection
* authentication
* rate limits
* retries
* fallback
* cost tracking
* logging
* routing

---

# LEVEL 17 — FINAL MONSTER PROJECT

We'll build a **production AI platform**, not another basic chatbot.

### Frontend

```text
Next.js
React
Vercel AI SDK
Streaming
Generative UI
```

### Backend

```text
Node.js
TypeScript
Zod
REST
AI Services
```

### AI

```text
LangChain.js
LangGraph.js
RAG
Tools
Agents
Structured Outputs
Memory
```

### Database

```text
PostgreSQL
pgvector
```

### Local Development

```text
ChromaDB
Docker
```

### Cloud

```text
Google Cloud
Cloud Run
Cloud SQL
```

### Production

```text
Security
Evaluation
Observability
Caching
Retries
Rate Limiting
Cost Control
```

---

# The Actual Priority

If we divide your learning effort:

```text
                    YOUR TIME
                       100%
                        │
           ┌────────────┴────────────┐
           │                         │
        FIRST 20%                 NEXT 80%
           │                         │
           ▼                         ▼
     ┌──────────────┐         ┌──────────────┐
     │ LLM          │         │ Advanced RAG  │
     │ Prompt       │         │ LangGraph     │
     │ Zod          │         │ Agents        │
     │ Tools        │         │ Memory        │
     │ Streaming    │         │ Multi-agent   │
     │ Embeddings   │         │ Multimodal    │
     │ RAG          │         │ Cloud         │
     │ LangChain    │         │ Security      │
     │ AI SDK       │         │ Evaluation    │
     └──────────────┘         │ Scaling       │
                              │ Optimization  │
                              └──────────────┘
```

But the **first 20% will not be rushed**.

We'll master it until you can build without blindly copying tutorials.

---

# One More Important Change

We will **not** follow:

```text
Module 1 → Module 2 → Module 3
```

just because that's the syllabus.

We'll follow:

```text
EASY
 ↓
UNDERSTAND
 ↓
BUILD
 ↓
BREAK
 ↓
FIX
 ↓
PRODUCTION
 ↓
ADVANCE
 ↓
MONSTER
```

For example, Tool Calling will first be:

```text
LLM
 ↓
Simple function
```

Then:

```text
LLM
 ↓
Typed tool
 ↓
Zod
```

Then:

```text
LLM
 ↓
Multiple tools
 ↓
Authorization
 ↓
Error handling
```

Then:

```text
LangChain Tool
```

Then:

```text
LangGraph Agent
```

Then:

```text
Persistent production agent
```

That's how we'll go from **zero → production engineer → AI architect** without drowning you in abstractions too early.

---

# Final Learning Ladder

```text
                         👹 MONSTER
                            │
                    AI ARCHITECT
                            │
               Production AI Systems
                            │
             ┌──────────────┴──────────────┐
             │                             │
        Agent Systems                 Cloud / Scale
             │                             │
        LangGraph                    Observability
             │                       Security
        LangChain                   Evaluation
             │
          RAG / Tools
             │
      Structured Output
             │
         Streaming
             │
        Prompting
             │
       LLM Fundamentals
             │
      TypeScript / Node
             │
             🟢 0
```

**We start at Level 0, move quickly through the JavaScript prerequisites, and then spend the majority of our early effort on the first high-value 20%: LLMs → prompts → Zod → structured output → streaming → tools → embeddings → RAG → LangChain → Vercel AI SDK.**

Every module will end with a **Hands-On Build Challenge**, and I'll wait for your implementation/questions before advancing.
