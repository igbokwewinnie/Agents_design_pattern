# 🤖 Agentic Design Patterns (From Scratch)

This repository is a **from-scratch implementation of four core Agentic Design Patterns**, built to deeply understand how modern AI agents reason, act, collaborate, and improve themselves.

Instead of relying on high-level frameworks like LangChain, CrewAI, or AutoGen, this project focuses on **first principles**: how agents are structured, how they think, and how they work together.

---

## 🧠 The Four Agentic Patterns Implemented

1. **Reflection Pattern**
2. **Tool Use Pattern**
3. **Planning Pattern (ReAct)**
4. **Multi-Agent Pattern**

Each pattern builds on the previous one.

Think of it like teaching an AI to:

* Think about its answers 🤔
* Use tools 🛠️
* Make plans 🗺️
* Work with other AIs 🤝

---

## 1️⃣ Reflection Pattern [Reflection Pattern Notebook](https://github.com/igbokwewinnie/Agents_design_pattern/blob/main/notebooks/reflection_pattern.ipynb)


Imagine you answer a question.
Then someone asks:

> “Are you sure? Can you improve this?”

You look at your answer again and fix it.

That’s **reflection**.

---

### 🔧 What This Pattern Does

* The agent produces an initial response
* The agent critiques its own answer
* The agent improves the answer based on that critique

---

### 🧩 Key Concepts in Code

* First LLM call → draft answer
* Second LLM call → critique
* Third LLM call → improved answer

This teaches the agent **self-improvement**.

---

### 💡 Why Reflection Matters

Reflection is how agents:

* Reduce hallucinations
* Improve reasoning
* Catch mistakes

Modern research agents rely heavily on this pattern.

---

## 2️⃣ Tool Use Pattern [Tool Use Pattern Notebook](https://github.com/igbokwewinnie/Agents_design_pattern/blob/main/notebooks/tool_pattern.ipynb)


Imagine an AI that can only talk.

Now imagine giving it:

* A calculator
* A file writer
* A database

Suddenly, it can **do things**, not just talk.

That’s tool use.

---

### 🔧 What This Pattern Does

* Tools are defined as Python functions
* Each tool has a JSON schema (arguments + types)
* The agent decides **when** and **how** to call a tool

---

### 🧩 Key Concepts in Code

* `@tool` decorator
* Automatic function signature extraction
* Argument validation before execution

Example:

```python
@tool
def write_str_to_txt(string_data: str, txt_filename: str):
    with open(txt_filename, 'w') as f:
        f.write(string_data)
```

---

### 💡 Why Tool Use Matters

Tool use turns LLMs into:

* Data processors
* File handlers
* System operators

This is the foundation of **real-world AI agents**.

---

## 3️⃣ Planning Pattern (ReAct) [Reflection Pattern Notebook](https://github.com/igbokwewinnie/Agents_design_pattern/blob/main/notebooks/reflection_pattern.ipynb)


Instead of answering immediately, the agent thinks like this:

1. 🤔 What do I need to do?
2. 🛠️ Should I use a tool?
3. 👀 What did the tool return?
4. 🤔 What’s next?

This loop continues until the task is done.

---

### 🔧 What This Pattern Does

Implements the **ReAct loop**:

```
Thought → Action → Observation → Thought → ... → Final Answer
```

---

### 🧩 Key Concepts in Code

* Explicit `Thought` logging
* Tool calling mid-reasoning
* Observations injected back into context

This is handled by the custom `ReactAgent`.

---

### 💡 Why Planning Matters

Planning allows agents to:

* Break problems into steps
* Handle complex workflows
* Adapt dynamically

This is the backbone of most agent frameworks.

---

## 4️⃣ Multi-Agent Collaboration Pattern [Multi-Agent Pattern Notebook](https://github.com/igbokwewinnie/Agents_design_pattern/blob/main/notebooks/multiagent_pattern.ipynb)


Instead of **one AI doing everything**, we use **a team**:

* One agent researches
* One agent processes
* One agent writes output

Just like humans working together.

---

### 🔧 What This Pattern Does

* Multiple agents with different roles
* Agents pass results to each other
* Execution follows dependencies

Inspired by:

* CrewAI (Crew + Agent)
* Airflow (DAGs & task dependencies)

---

### 🧩 Key Concepts in Code

#### Agent Dependencies

```python
agent_1 >> agent_2 >> agent_3
```

Meaning:

* Agent 2 waits for Agent 1
* Agent 3 waits for Agent 2

---

#### Crew (DAG Manager)

* Automatically registers agents
* Topologically sorts them
* Executes them in the correct order

---

### 💡 Why Multi-Agent Systems Matter

This pattern enables:

* Scalability
* Specialization
* Complex pipelines

It’s how modern AI systems operate at scale.

---

## 🧱 Architecture Overview

```
User Task
   ↓
Planning Agent (ReAct)
   ↓
Tool Agents
   ↓
Reflection Agent
   ↓
Multi-Agent Crew Output
```

---

## 🚀 Why This Project Matters

This repository shows:

* Deep understanding of agent internals
* Framework-independent design
* Production-style architecture

It is ideal for:

* ML / AI Engineer roles
* Research Engineer roles
* Agentic AI projects

---
🚀 Installation
1. Clone the Repository
```
git clone https://github.com/yourusername/agents_design_pattern.git
cd agents_design_pattern
```
2. Set Up Environment Variables
Create a .env file in the project root:
```
GROQ_API_KEY=your_groq_api_key_here
```

---

## 🙏 Acknowledgements

This project was inspired by a course taught by **[The Neural Maze](https://github.com/neural-maze/agentic-patterns-course?tab=readme-ov-file)**.  
Their clear explanations and hands-on teaching style played a key role in my understanding of agentic design patterns and multi-agent systems.


---

⭐ If you found this useful, give the repo a star!
