# Week 2: Retrieval-Augmented Generation (RAG) and Evaluations

## 📖 Overview

Week 2 dives deep into the world of Retrieval-Augmented Generation (RAG) systems and their evaluation. Building on Week 1's foundation with LLMs, we now explore how to enhance LLM capabilities by grounding them in external knowledge sources. This week covers building RAG systems from scratch, understanding production-ready patterns, and implementing robust evaluation frameworks to measure and improve system performance.

## 🎯 Learning Objectives

By the end of this week, you will:

- **Understand RAG Fundamentals:** Master the core components of RAG systems (retrieval, augmentation, generation)
- **Build from Scratch:** Implement a complete RAG pipeline without frameworks to understand the mechanics
- **Production Patterns:** Learn industry-standard tools and patterns (LangChain, LangGraph, vector databases)
- **Evaluation Frameworks:** Apply systematic evaluation using RAGAS and synthetic data generation
- **Advanced Retrieval:** Explore sophisticated retrieval strategies beyond naive similarity search
- **Optimize Performance:** Measure, compare, and improve RAG system performance

## 📅 Week Structure

### Day 3: RAG Foundations
**Focus:** Understanding and implementing RAG from first principles

**Topics:**
- Embeddings and cosine similarity
- Building a vector database from scratch
- Document chunking strategies
- Basic RAG pipeline implementation
- Introduction to production RAG with LangChain/LangGraph
- LangSmith for observability and tracing

**Key Activities:**
- Implement vector search manually
- Build a complete RAG system
- Set up LangSmith monitoring
- Create evaluation datasets

**Files:**
- `1_Basic_RAG.ipynb` - From-scratch RAG implementation
- `2_Production_RAG.ipynb` - LangChain/LangGraph patterns

---

### Day 4: Evaluation and Testing
**Focus:** Measuring and validating RAG system performance

**Topics:**
- Why evaluation matters in RAG systems
- RAGAS framework and metrics
  - Faithfulness
  - Answer Relevancy
  - Context Precision
  - Context Recall
  - Answer Correctness
- Synthetic Data Generation (SDG)
- Multi-query retrieval strategies
- A/B testing RAG architectures

**Key Activities:**
- Generate synthetic test datasets
- Evaluate RAG pipelines with RAGAS
- Compare baseline vs. advanced retrievers
- Measure improvement systematically

**Files:**
- `1-ragas.ipynb` - RAGAS evaluation framework
- `2-SDG.ipynb` - Synthetic data generation

---

### Day 5: Advanced Retrieval Techniques
**Focus:** Going beyond naive similarity search

**Topics:**
- Naive retrieval limitations
- BM25 (Best Matching 25) algorithm
- Multi-query retrieval
- Parent-document retrieval
- Contextual compression and reranking
- Ensemble retrieval methods
- Semantic chunking strategies

**Key Activities:**
- Implement multiple retrieval strategies
- Compare performance across methods
- Evaluate with RAGAS metrics
- Optimize for specific use cases

**Files:**
- `1-advanced_retrievers.ipynb` - Advanced retrieval patterns

## 🔑 Key Concepts

### RAG Architecture
```
User Query → [Embedding] → Vector Search → Context Retrieval
                                                ↓
User Query + Retrieved Context → [LLM] → Generated Answer
```

### Core Components

1. **Retrieval (R)**
   - Document loading and preprocessing
   - Text chunking strategies
   - Embedding generation
   - Vector storage and search
   - Distance metrics (cosine similarity, etc.)

2. **Augmentation (A)**
   - Context injection into prompts
   - Prompt engineering for RAG
   - Context window management
   - Metadata utilization

3. **Generation (G)**
   - LLM selection and configuration
   - Response synthesis
   - Output parsing
   - Error handling

### Evaluation Metrics

- **Faithfulness:** Is the answer grounded in the retrieved context?
- **Answer Relevancy:** Does the answer address the question?
- **Context Precision:** Are the top-ranked contexts relevant?
- **Context Recall:** Are all relevant contexts retrieved?
- **Answer Correctness:** Semantic + factual correctness vs. ground truth

## 🛠️ Technical Stack

- **LLMs:** OpenAI GPT-4o-mini, GPT-3.5-turbo
- **Embeddings:** `text-embedding-3-small`, `text-embedding-ada-002`
- **Vector Stores:** QDrant (in-memory)
- **Frameworks:** LangChain, LangGraph
- **Evaluation:** RAGAS
- **Observability:** LangSmith
- **Reranking:** Cohere Rerank API
- **Package Manager:** `uv`

## 📊 Datasets

- **Noli Me Tangere** (Day 3) - Classic Philippine novel for basic RAG
- **Jose Rizal Writings** (Day 3) - Historical documents for production RAG
- **Lord of the Rings** (Day 4) - Book One for evaluation
- **Loan Complaints** (Day 5) - Structured complaint data for advanced retrieval

## 💡 Key Insights and Patterns

### Week 2 Highlights

1. **RAG is About Retrieval Quality**
   - The quality of retrieved context directly impacts answer quality
   - Advanced retrieval strategies can dramatically improve performance
   - Different queries benefit from different retrieval methods

2. **Evaluation is Non-Negotiable**
   - "You cannot improve what you cannot measure"
   - Synthetic data generation enables systematic testing
   - Multiple metrics provide comprehensive assessment

3. **Production-Ready Patterns**
   - Observability and tracing are essential
   - Modular architecture enables experimentation
   - Vector databases scale better than naive approaches

4. **Trade-offs are Everywhere**
   - Chunk size affects both relevance and coherence
   - More context isn't always better
   - Retrieval speed vs. accuracy
   - Cost vs. performance

## 🎓 Prerequisites

- Completion of Week 1 (LLM fundamentals, prompt engineering)
- OpenAI API key
- Cohere API key (for Day 5 reranking)
- LangSmith account (optional but recommended)
- Python environment with `uv` configured

## 📚 Additional Resources

### Documentation
- [LangChain RAG](https://python.langchain.com/docs/use_cases/question_answering/)
- [RAGAS Documentation](https://docs.ragas.io/)
- [LangSmith](https://docs.smith.langchain.com/)
- [QDrant](https://qdrant.tech/documentation/)
- [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings)

### Research Papers
- ["Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks"](https://arxiv.org/abs/2005.11401)
- ["Lost in the Middle: How Language Models Use Long Contexts"](https://arxiv.org/abs/2307.03172)

### Community Resources
- AI Makerspace materials
- LangChain community examples
- RAGAS GitHub repository

## 🚀 Getting Started

1. **Set up environment:**
   ```bash
   cd week_2_rag_and_evals/day_3
   uv pip install -r requirements.txt
   ```

2. **Configure API keys:**
   - OpenAI API key
   - LangSmith API key (optional)
   - Cohere API key (for Day 5)

3. **Start with Day 3:**
   - Open `1_Basic_RAG.ipynb`
   - Follow the guided activities
   - Complete the questions and reflections

4. **Progress sequentially:**
   - Each day builds on previous concepts
   - Complete notebooks in order
   - Review reflections to consolidate learning

## 🎯 Success Criteria

By the end of Week 2, you should be able to:

- ✅ Build a RAG system from scratch
- ✅ Implement production-ready RAG with LangChain
- ✅ Generate synthetic test datasets
- ✅ Evaluate RAG systems using RAGAS
- ✅ Implement and compare multiple retrieval strategies
- ✅ Optimize RAG performance through measurement
- ✅ Explain trade-offs in RAG architecture decisions

## 📝 Assessment Approach

Each day includes:
- **Guided questions** embedded in notebooks
- **Hands-on activities** with expected outcomes
- **Reflection sections** for consolidating learning
- **Comparative analysis** of different approaches

## 🤝 Collaboration

This week emphasizes:
- Breakout room discussions
- Group observations and comparisons
- Shared insights on retrieval strategies
- Collaborative evaluation analysis

---

**Next Steps:** Proceed to [Day 3](day_3/README.md) to begin your RAG journey!

**Previous Week:** [Week 1: Intro & Vibe Coding](../week_1_intro_vibe_coding/README.md)
