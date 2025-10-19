# AI/LLM Engineering Cohort #2 - PSI AI Academy

Welcome to my learning journey in the AI/LLM Engineering Cohort #2 at PSI AI Academy!

## 📚 Repository Structure

This repository is organized by weeks and days to track my progress throughout the cohort:

```
/week_1_intro_vibe_coding/
├── day_1/ - Introduction to LLMs
├── day_2/ - Vibe Coding Applications
└── README.md

/week_2_[topic]/
├── day_1/
├── day_2/
└── README.md

... (additional weeks)
```

## 🚀 Setup Instructions

### Prerequisites
- Python 3.10 or higher
- [uv](https://github.com/astral-sh/uv) - Fast Python package installer and resolver

### Installing uv

**Windows (PowerShell):**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Project Setup

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd ai-llm-cohort2
   ```

2. **Create and activate virtual environment:**
   ```bash
   # uv will automatically create a virtual environment
   uv venv
   
   # Activate the environment
   # Windows
   .venv\Scripts\activate
   
   # macOS/Linux
   source .venv/bin/activate
   ```

3. **Install dependencies for a specific week:**
   ```bash
   cd week_1_intro_vibe_coding
   uv pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   - Copy `.env.example` to `.env` in the relevant week folder
   - Add your API keys and configuration

## 📖 Weekly Progress

### Week 1: Introduction & Vibe Coding ✅
**Status:** Completed | **Dates:** October 19, 2025

#### Day 1: Prompt Engineering Techniques
- ✅ Implemented Zero-Shot, Few-Shot, and Chain of Thought prompting
- ✅ Improved model accuracy from 0% to 100% on reasoning tasks
- ✅ Completed `01-jayr-day-1.ipynb` with comprehensive solutions
- **Key Learning:** Structured prompts dramatically improve LLM output quality

#### Day 2: Vibe Coding Application - HR Resume Screener
- ✅ Built MVP using Replit AI Agent from Product Requirements Document
- ✅ Implemented Design Thinking methodology (Empathize → Define → Ideate → Prototype → Test)
- ✅ Created AI-powered resume screening app with "vibe scores"
- ✅ Documented real-world challenges (build limits, API security, state management)
- **Key Learning:** Vibe coding = AI acceleration + human guidance

**Technologies:** OpenAI GPT-4, LangChain, Replit AI Agent, Flask, Streamlit, Python

---

### Week 2: [Topic Coming Soon]
*To be updated as cohort progresses*

## 🔑 Environment Variables

Each week may require specific API keys and configurations. Create a `.env` file in the week directory with:

```env
# OpenAI API Key
OPENAI_API_KEY=your_api_key_here

# Other API keys as needed
ANTHROPIC_API_KEY=your_api_key_here
```

⚠️ **Never commit `.env` files to version control!**

## 📝 Learning Reflections

### Week 1 Highlights

**What Worked Well:**
- Clear documentation accelerated learning and development
- AI-assisted coding (vibe coding) significantly reduced boilerplate time
- Design Thinking framework kept focus on user problems vs. technology solutions
- Prompt engineering techniques showed immediate, measurable improvements

**Challenges & Solutions:**
- **Challenge:** Simple reasoning tasks failed without proper prompting structure
  - **Solution:** Applied Chain of Thought prompting for step-by-step reasoning
- **Challenge:** Replit Agent hit build limits during testing
  - **Solution:** Documented progress, pivoted to local development
- **Challenge:** Managing API keys securely across platforms
  - **Solution:** Used environment variables and .gitignore best practices

**Key Takeaways:**
1. Structure and clarity in prompts = Better AI outputs
2. Vibe coding requires active guidance, not passive acceptance
3. Well-documented requirements lead to better AI-generated code
4. Always have backup development environments
5. Explainability matters more than accuracy for user trust

Each day includes detailed `README.md` files with:
- Key concepts learned
- Challenges encountered
- Solutions discovered
- Resources used
- Personal reflections

## 🛠️ Tech Stack

- **Language:** Python 3.10+
- **Package Management:** uv
- **LLM Providers:** OpenAI, Anthropic, and others
- **Notebooks:** Jupyter/IPython
- **Web Framework:** Streamlit/Flask (varies by project)

## 📧 Contact

For questions or collaboration:
- **Cohort:** AI/LLM Engineering Cohort #2
- **Institution:** PSI AI Academy

## 📄 License

This repository contains personal learning materials from the PSI AI Academy cohort.

---

*Last Updated: October 19, 2025*
