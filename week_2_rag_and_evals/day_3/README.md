# Day 3: RAG Foundations - From Scratch to Production

## 📖 Overview

Day 3 introduces Retrieval-Augmented Generation (RAG) systems, starting with first-principles implementation and progressing to production-ready patterns. You'll build a complete RAG pipeline from scratch to understand the underlying mechanics, then learn how professional frameworks streamline the process.

## 🎯 Objectives

- Understand how embeddings capture semantic meaning
- Implement cosine similarity for semantic search
- Build a vector database from scratch
- Create a complete RAG pipeline without frameworks
- Learn production RAG patterns with LangChain and LangGraph
- Set up observability and tracing with LangSmith
- Generate and evaluate test datasets

## 📝 Activities

### Notebook 1: Basic RAG - From Scratch (`1_Basic_RAG.ipynb`)

**Learning Path:**
1. **Embeddings Exploration**
   - Understanding text-embedding-3-small
   - Computing cosine similarity
   - Exploring semantic relationships

2. **Document Processing**
   - Loading source documents (Noli Me Tangere text)
   - Chunking strategies (CharacterTextSplitter)
   - Understanding chunk size trade-offs

3. **Vector Database Construction**
   - Building a dictionary-based vector store
   - Async embedding generation for efficiency
   - Implementing semantic search

4. **RAG Pipeline Assembly**
   - Retrieving relevant context
   - Augmenting prompts with context
   - Generating grounded responses

**Key Questions Answered:**
- ✅ How does cosine similarity measure semantic relatedness?
- ✅ Can embedding dimensions be modified? (Answer: Yes, via dimensionality reduction)
- ✅ What technique does OpenAI use? (Answer: Matryoshka Representation Learning)
- ✅ Why use async for embeddings? (Answer: Parallel API calls, improved throughput)

### Notebook 2: Production RAG (`2_Production_RAG.ipynb`)

**Learning Path:**
1. **LangChain Integration**
   - DirectoryLoader for PDF documents
   - RecursiveCharacterTextSplitter with token counting
   - QDrant vector store setup

2. **LangGraph Pipeline**
   - State management with TypedDict
   - Sequential node execution
   - Retriever and generator nodes

3. **LangSmith Observability**
   - Setting up tracing
   - Monitoring LLM calls
   - Debugging RAG pipelines

4. **Dataset Creation**
   - Generating test questions
   - Creating evaluation datasets
   - Preparing for RAGAS evaluation

**Key Questions Answered:**
- ✅ Why does the model hallucinate on out-of-context questions?
- ✅ How to improve prompt to stay within context?
- ✅ What are the benefits of observability in production?

## 🔍 Key Concepts Learned

### RAG Architecture

```
┌─────────────┐
│ User Query  │
└──────┬──────┘
       │
       ▼
┌─────────────────────────────────┐
│  1. Embedding Generation        │
│     (text-embedding-3-small)    │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  2. Vector Search               │
│     (Cosine Similarity)         │
│     → Top K most similar chunks │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  3. Context Augmentation        │
│     Query + Retrieved Docs      │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  4. LLM Generation              │
│     (GPT-4o-mini)               │
└─────────────┬───────────────────┘
              │
              ▼
┌─────────────────────────────────┐
│  Grounded Answer                │
└─────────────────────────────────┘
```

### Embeddings and Similarity

**Cosine Similarity Formula:**
$$
\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}
$$

**Key Properties:**
- Range: [-1, 1] (typically [0, 1] for text embeddings)
- 1.0 = identical meaning
- 0.0 = no relationship
- Captures semantic similarity, not just lexical overlap

### Chunking Strategies

**Trade-offs:**

| Aspect | Small Chunks (200-500 tokens) | Large Chunks (1000-2000 tokens) |
|--------|-------------------------------|----------------------------------|
| **Precision** | High - focused content | Lower - more noise |
| **Context** | Less context | More complete context |
| **Relevance** | Very specific | Broader coverage |
| **Storage** | More chunks, more cost | Fewer chunks |
| **Best For** | Q&A, fact lookup | Summarization, reasoning |

### Vector Database Fundamentals

**From-Scratch Implementation:**
```python
class VectorDatabase:
    def __init__(self):
        self.vectors = defaultdict(np.array)  # text -> vector
    
    def insert(self, text, embedding):
        self.vectors[text] = np.array(embedding)
    
    def search(self, query_embedding, k=5):
        # Compute similarity with all vectors
        # Return top k matches
```

**Production Implementation (QDrant):**
- Efficient ANN (Approximate Nearest Neighbor) search
- Persistent storage
- Horizontal scaling
- Advanced filtering capabilities

### LangChain/LangGraph Patterns

**State-Based RAG with LangGraph:**
```python
class State(TypedDict):
    question: str
    context: list[Document]
    response: str

def retrieve(state: State) -> State:
    # Retrieval logic
    return {"context": retrieved_docs}

def generate(state: State) -> State:
    # Generation logic
    return {"response": answer}

graph = StateGraph(State)
graph.add_sequence([retrieve, generate])
```

**Benefits:**
- Clear state transitions
- Easy debugging
- Modular components
- Testable units

## 💡 Interesting Findings

### Top 3 RAG Insights from Day 3

#### 1. **Async is Essential for Production** ⭐⭐⭐

**Why it matters:**
- Embedding 100 documents sequentially: ~30 seconds
- Embedding 100 documents async: ~3 seconds (10x faster!)
- OpenAI API allows concurrent requests
- Critical for batch processing and user experience

**Implementation:**
```python
async def async_get_embeddings(texts: List[str]):
    tasks = [get_embedding(text) for text in texts]
    return await asyncio.gather(*tasks)
```

---

#### 2. **Embedding Dimension Flexibility** ⭐⭐⭐

**Discovery:**
- `text-embedding-3-small` default: 1536 dimensions
- Can be reduced to 512, 256, etc. via API parameter
- Uses Matryoshka Representation Learning
- Enables storage optimization with minimal quality loss

**Use Cases:**
- Memory-constrained deployments
- Cost optimization (storage + compute)
- Faster search with acceptable accuracy trade-off

---

#### 3. **Prompt Engineering for Grounding** ⭐⭐⭐

**The Problem:**
- Models tend to answer from general knowledge
- Can hallucinate when context is insufficient

**The Solution:**
```
Use ONLY the provided context to answer.
If the answer is not in the context, respond: "I don't know"
```

**Impact:**
- Reduces hallucination significantly
- Improves trustworthiness
- Makes RAG behavior more predictable

## 📊 Evaluation Results

### From-Scratch RAG Performance

**Test Query:** "Who is Capitan Tiago?"

**Retrieved Contexts:** 5 chunks
**Response Time:** ~2.3 seconds
**Answer Quality:** Accurate, grounded in text

**Observations:**
- Semantic search successfully found relevant passages
- Cosine similarity threshold of 0.7+ yielded good results
- Context length ~1500 tokens provided sufficient information

### Production RAG Performance

**Test Query:** "Who is Capitan Tiago?"

**Retrieved Contexts:** 4 chunks
**Response Time:** ~1.8 seconds
**Answer Quality:** Accurate, concise

**Improvements:**
- QDrant's ANN search is faster than brute-force
- Metadata enrichment enables filtering
- LangSmith provides visibility into bottlenecks

## 🛠️ Tools & Technologies

### Core Libraries
```toml
[dependencies]
openai = "^1.0.0"
langchain = "^0.1.0"
langchain-openai = "^0.0.2"
langchain-community = "^0.0.13"
langgraph = "^0.0.20"
qdrant-client = "^1.7.0"
numpy = "^1.24.0"
tiktoken = "^0.5.0"
nest-asyncio = "^1.5.8"
```

### Custom Utilities
- `psi.text_utils.TextFileLoader` - Document loading
- `psi.text_utils.CharacterTextSplitter` - Text chunking
- `psi.vectordatabase.VectorDatabase` - Simple vector store
- `psi.openai_utils.EmbeddingModel` - Embedding wrapper

### APIs Used
- OpenAI Embeddings API (`text-embedding-3-small`)
- OpenAI Chat API (`gpt-4o-mini`)
- LangSmith Tracing API (optional)

## 🎯 Hands-On Activities Completed

### Activity #1: Explore Embeddings and Cosine Similarity
- [x] Implement cosine similarity function
- [x] Generate embeddings for test sentences
- [x] Compare similarity scores
- [x] Understand semantic vs. lexical similarity

**Key Finding:** "I love puppies!" and "Bayang magiliw!" have low similarity (~0.15) despite same sentence structure, because semantics differ.

### Activity #2: Build RAG Pipeline
- [x] Load and chunk documents
- [x] Generate embeddings for all chunks
- [x] Implement vector search
- [x] Create prompt template
- [x] Generate grounded responses

**Key Finding:** Chunk size of 400-600 characters balances context and precision effectively.

### Breakout Room Discussions

**Question:** How does cosine similarity work?

**Group Observations:**
- Measures angle between vectors, not magnitude
- Normalized dot product
- Semantic similarity correlates with vector proximity
- Works well for high-dimensional embeddings (1536-D)

**Question:** Why did the model answer even when not related to Jose Rizal?

**Group Insights:**
- Model defaults to general knowledge
- Prompt needs explicit constraint: "Answer ONLY from context"
- Temperature=0 reduces creativity but doesn't prevent hallucination
- Need to check if context is relevant before answering

## 🚀 Next Steps

After completing Day 3:

1. **Review Your Answers:**
   - Check understanding of embedding dimensionality
   - Confirm grasp of async benefits
   - Ensure prompt engineering insights are clear

2. **Experiment:**
   - Try different chunk sizes (200, 500, 1000 tokens)
   - Test various embedding models
   - Modify prompts to improve grounding

3. **Prepare for Day 4:**
   - Understand that evaluation is critical
   - Recognize need for systematic measurement
   - Be ready to generate synthetic test data

4. **Optional Deep Dive:**
   - Explore LangSmith traces in detail
   - Implement custom retrieval scoring
   - Try different distance metrics (Euclidean, dot product)

## 📚 Resources Referenced

### Documentation
- [OpenAI Embeddings Guide](https://platform.openai.com/docs/guides/embeddings)
- [Matryoshka Embeddings Paper](https://arxiv.org/abs/2205.13147)
- [LangChain RAG Tutorial](https://python.langchain.com/docs/use_cases/question_answering/)
- [QDrant Documentation](https://qdrant.tech/documentation/)
- [LangSmith Setup Guide](https://docs.smith.langchain.com/)

### Code References
- AI Makerspace PSI utilities
- LangChain LCEL patterns
- LangGraph state management examples

## 🎓 Reflection Section

### What I Learned Today

**Technical Skills:**
- Implemented vector search from scratch
- Understood embedding generation and storage
- Built production RAG with LangChain/LangGraph
- Set up observability with LangSmith

**Conceptual Understanding:**
- RAG addresses LLM knowledge cutoff and hallucination
- Retrieval quality is paramount
- Chunking strategy significantly impacts performance
- Async processing is essential for production

**Surprises:**
- Cosine similarity is computationally simple yet powerful
- Embedding dimensions can be flexibly reduced
- LangGraph makes state management intuitive
- Prompt engineering for grounding is critical

### Challenges Encountered

1. **Chunk Size Selection:** Finding optimal balance required experimentation
2. **Async Complexity:** Understanding event loops and nest_asyncio
3. **Context Window Management:** Ensuring retrieved context fits within LLM limits
4. **Grounding vs. Knowledge:** Preventing model from using parametric knowledge

### Questions for Further Exploration

- How do different distance metrics compare for text search?
- What's the optimal chunk size for different document types?
- How to handle multi-modal documents (text + images)?
- When should we use semantic vs. keyword search?

---

**Progress Summary:**
- ✅ Completed basic RAG implementation from scratch
- ✅ Built production RAG with LangChain/LangGraph
- ✅ Set up LangSmith observability
- ✅ Generated evaluation datasets
- ✅ Answered all guided questions
- ✅ Ready for Day 4: Evaluation with RAGAS

**Next:** [Day 4: RAGAS and Synthetic Data Generation](../day_4/README.md)
