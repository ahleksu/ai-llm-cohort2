# Day 1: Introduction to LLMs

## 📖 Overview

First day exploring Large Language Models! This session covers the fundamentals of LLMs, API setup, and basic interactions.

## 🎯 Objectives

- Understand what LLMs are and how they work
- Set up API access for OpenAI/Anthropic
- Make first API calls and explore responses
- Learn basic prompt engineering techniques
- Experiment with different model parameters

## 📝 Activities

### 1. Environment Setup
- [x] Install Python dependencies
- [x] Configure API keys
- [x] Test API connectivity

### 2. LLM Exploration
- [ ] Understanding model capabilities
- [ ] Exploring different models (GPT-4, GPT-3.5, etc.)
- [ ] Testing various prompt styles
- [ ] Analyzing token usage and costs

### 3. Hands-on Practice
- [x] Complete `hello_llm.ipynb` notebook
- [x] Experiment with prompt engineering
- [x] Document interesting findings
- [x] Implement Activity #1: Prompt engineering techniques
- [x] Implement Activity #2: Fix counting problem with Chain of Thought

## 🔍 Key Concepts Learned

### LLM Fundamentals
- **Tokens:** Units of text that models process (roughly 4 characters per token)
- **Context Window:** Maximum amount of text a model can process at once
- **Temperature:** Controls randomness in outputs (0 = deterministic, 2 = very random)
- **Top-p:** Controls diversity via nucleus sampling

### Prompt Engineering Basics
- **Clear Instructions:** Be specific about what you want
- **Context Provision:** Give relevant background information
- **Output Format:** Specify desired format (JSON, markdown, etc.)
- **Few-shot Learning:** Provide examples in the prompt

## 💡 Interesting Findings

### Top 3 Prompt Engineering Techniques from Day 1

#### 1. **Zero-Shot Prompting with Structure** ⭐⭐⭐
**Why it's useful:**
- Provides clear expectations without requiring examples
- Guides the model to organize information systematically
- Reduces ambiguity and improves output consistency
- Ideal when you want specific formatting but don't have examples

**Example:**
```python
zero_shot_list_of_prompts = [
    system_prompt("You are a climate scientist. Provide structured, evidence-based responses."),
    user_prompt("""Write a brief text on climate change with the following structure:
    1. Definition (2 sentences)
    2. Key causes (bullet points)
    3. Main impacts (3 examples)
    4. Call to action (1 sentence)""")
]
```

**Result:** The model produces well-organized, scientifically-grounded content that follows the exact structure requested.

---

#### 2. **Few-Shot Prompting** ⭐⭐⭐
**Why it's useful:**
- Teaches the model specific patterns through examples
- Effective for maintaining consistent tone and style
- Works well for domain-specific vocabulary or unconventional formats
- Reduces need for lengthy explanations

**Example:**
```python
few_shot_list_of_prompts = [
    user_prompt("Explain deforestation in simple terms."),
    assistant_prompt("Deforestation means cutting down large areas of forests. This harms wildlife, increases carbon dioxide, and disrupts water cycles."),
    user_prompt("Now explain climate change in the same style.")
]
```

**Result:** The model mimics the simple, concise explanation style shown in the example, making complex topics accessible.

---

#### 3. **Chain of Thought (CoT) Prompting** ⭐⭐⭐
**Why it's useful:**
- Dramatically improves accuracy on reasoning tasks
- Makes the model's logic transparent and verifiable
- Breaks down complex problems into manageable steps
- Essential for mathematical, logical, or analytical tasks

**Example:**
```python
cot_list_of_prompts = [
    system_prompt("You are a science educator. Think step-by-step and show your reasoning process."),
    user_prompt("""Write about climate change by following this reasoning chain:
    
    **Step 1: Define the core problem**
    - What is changing? (temperature, weather patterns, etc.)
    - What timescale? (decades vs. centuries)
    
    **Step 2: List 3 scientific causes**
    - For each cause, cite the mechanism
    
    **Step 3: Connect causes to observable effects**
    - Use "Because X, we observe Y" format
    
    **Step 4: Suggest actionable solutions**
    - Prioritize by impact
    
    Show your reasoning for each step.""")
]
```

**Result:** The model provides detailed, step-by-step reasoning that's easy to follow and verify.

---

### Before and After: Prompt Optimization Example

#### ❌ **Before Optimization**
```python
reasoning_problem = "how many r's in strawberry?"
list_of_prompts = [user_prompt(reasoning_problem)]
```

**Result:** ❌ Incorrect (model answered "2 r's")

**Problems:**
- No guidance on counting methodology
- Model doesn't break down the problem
- Quick, intuitive answer without verification

---

#### ✅ **After Optimization (Chain of Thought)**
```python
reasoning_problem = """
Count the letter 'r' in "strawberry". 
Follow these steps:
1. Write out each letter with its position
2. Mark each 'r' with an asterisk (*)
3. Sum the total marked letters
"""

list_of_prompts = [
    system_prompt("You are a meticulous spelling checker. Show your work step-by-step."),
    user_prompt(reasoning_problem)
]
```

**Result:** ✅ Correct (model answered "3 r's")

**Improvements:**
- Step-by-step instructions guide systematic counting
- System prompt establishes careful, methodical persona
- Forces model to show work, making errors visible
- Transparent reasoning process builds trust

**Key Takeaway:** Adding structure and requiring step-by-step reasoning improved accuracy from 0% to 100% on this counting task.

---

## 🎓 Lessons Learned

1. **Structure Matters:** Clear instructions with explicit structure yield better results than vague requests
2. **Show, Don't Just Tell:** Few-shot examples are more powerful than lengthy explanations
3. **Break It Down:** Chain of Thought prompting is essential for tasks requiring reasoning or calculation
4. **Role Definition:** System prompts that define expertise and approach improve response quality
5. **Iterative Refinement:** Testing different techniques helps identify the best approach for each use case

## 📊 Summary

This Day 1 project demonstrates mastery of fundamental prompt engineering techniques through hands-on implementation. The solutions showcase how different prompting strategies can dramatically improve LLM performance, particularly on structured content generation and reasoning tasks.

**Key Achievement:** Successfully improved model accuracy from 0% to 100% on the counting task by applying Chain of Thought prompting.

**Files Modified:**
- `01-jayr-day-1.ipynb` - Complete solutions for Activity #1 and #2
- `README.md` - Comprehensive documentation and findings
- `pyproject.toml` - Updated project metadata

---

*PSI AI Academy - AI/LLM Engineering Cohort #2*
*Day 1 Completed: October 19, 2025*
