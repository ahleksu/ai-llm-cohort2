# Week 1: Introduction & Vibe Coding

## 🎯 Week Overview

This week introduces the fundamentals of Large Language Models (LLMs) and explores "vibe coding" - an intuitive approach to building applications with AI assistance.

## 📅 Daily Breakdown

### Day 1: Introduction to LLMs
**Focus:** Understanding LLM basics, API interactions, and prompt engineering

**Activities:**
- Setting up development environment
- First interactions with LLMs
- Basic prompt engineering techniques
- Exploring model capabilities and limitations

**Deliverables:**
- `hello_llm.ipynb` - Interactive notebook exploring LLM basics

### Day 2: Vibe Coding Application
**Focus:** Building a practical application using LLM APIs

**Activities:**
- Designing an LLM-powered application
- Implementing API integrations
- Creating a user interface
- Testing and iteration

**Deliverables:**
- `vibe_coding_app/` - Complete application with source code

## 🛠️ Setup

1. **Navigate to the week directory:**
   ```bash
   cd week_1_intro_vibe_coding
   ```

2. **Install dependencies:**
   ```bash
   uv pip install -r requirements.txt
   ```

3. **Configure environment variables:**
   ```bash
   cp .env.example .env
   # Edit .env with your API keys
   ```

4. **Run Jupyter for notebooks:**
   ```bash
   jupyter notebook
   ```

5. **Run Day 2 application:**
   ```bash
   cd day_2/vibe_coding_app
   python app.py
   ```

## 📚 Key Concepts

- **LLM Fundamentals:** Understanding how large language models work
- **API Integration:** Working with OpenAI, Anthropic, and other APIs
- **Prompt Engineering:** Crafting effective prompts for desired outputs
- **Vibe Coding:** Iterative development with AI assistance
- **Error Handling:** Managing API failures and edge cases

## 🔑 Required API Keys

- OpenAI API Key (GPT models)
- [Optional] Anthropic API Key (Claude models)

## 📊 Learning Outcomes

By the end of this week, you should be able to:
- [x] Set up and configure LLM API access
- [x] Write effective prompts for various tasks
- [x] Build a simple LLM-powered application
- [x] Handle API responses and errors
- [x] Understand token limits and cost considerations
- [x] Apply Design Thinking methodology to AI projects
- [x] Use vibe coding to accelerate development
- [x] Document AI development processes comprehensively

## 🤔 Reflections

### What Went Well
- **Day 1 Success:** Successfully implemented all three prompt engineering techniques (Zero-Shot, Few-Shot, Chain of Thought)
- **Improved Accuracy:** Achieved 100% accuracy on reasoning tasks by applying structured prompting
- **Real-World Application:** Day 2's Vibe Coding app addressed actual HR department pain points
- **AI-Assisted Development:** Replit AI Agent autonomously generated ~600 lines of working code from PRD
- **Rapid Prototyping:** Went from concept to functional UI in under 20 minutes using vibe coding

### Challenges Faced
- **Reasoning Tasks:** Initial prompts failed on simple counting tasks until applying Chain of Thought
- **Platform Limits:** Hit Replit's free tier agent build limits during testing phase
- **API Integration:** Managing API key security and environment variables across different platforms
- **State Management:** Understanding Streamlit's reactive model for session persistence
- **AI Over-Engineering:** Replit Agent occasionally added features not specified in requirements

### Key Takeaways
1. **Structure Drives Success:** Clear, structured prompts dramatically improve LLM output quality
2. **Show Your Work:** Chain of Thought prompting is essential for reasoning and calculation tasks
3. **PRD Quality Matters:** Well-documented requirements lead to better AI-generated code
4. **Vibe Coding ≠ Zero Effort:** AI accelerates development but requires human guidance and validation
5. **Explainability Builds Trust:** Users need to understand AI decisions, especially in HR contexts
6. **Platform Constraints:** Always understand tool limitations before committing to a development platform

### Resources Used
- [OpenAI API Documentation](https://platform.openai.com/docs) - API reference and best practices
- [Replit AI Agent](https://replit.com) - AI-powered code generation platform
- [Streamlit Documentation](https://docs.streamlit.io/) - Python web app framework
- [LangChain Documentation](https://python.langchain.com/) - LLM application framework
- PSI AI Academy course materials and peer discussions

---

*Week 1: October 19, 2025*
