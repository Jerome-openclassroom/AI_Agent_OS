# 🖥️ AI Orchestrator Agent — Proof of Concept

This project demonstrates a **local AI agent** capable of interpreting natural language commands, generating **structured XML instructions**, and executing **real OS actions** such as creating folders or files and writing content inside them.

At its core, this system showcases how **future operating systems** could be driven entirely by natural language prompts, where the user expresses intent and the AI safely orchestrates the required actions — no manual navigation, no file dialog boxes, just intelligent automation.

---

## 📂 Project Structure

```
.
├── README.md                         ← This file (English)
├── README_Fr.md                      ← French version of the README
├── code/
│   ├── HelloWorld_AI_Agent.ipynb     ← First version (pure Python + OpenAI API)
│   ├── AI_Agent_Langchain.ipynb      ← Modular LangChain version
│   └── System_instruction.txt        ← Hardened system prompt (XML spec, rules, few-shots)
└── screenshot/
    └── demo.gif                      ← Animated demo: folder creation + file write via prompt

```

---

## 🚀 Features

- **Natural Language Interface** — Ask the agent to create folders or files, and it generates structured XML instructions.
- **Strict Output Format** — XML `<orchestrator>` block is machine-parsable and safe.
- **Local Execution** — Python code parses XML and executes the requested action on your machine.
- **Two Implementations**:
  - *HelloWorld_AI_Agent.ipynb*: minimal direct OpenAI API usage.
  - *AI_Agent_Langchain.ipynb*: modular LangChain chain, cleaner separation of components.
- **Gradio UI** — Run locally or share via public link (`share=True`) for demonstration.

---

## 🧠 How It Works

1. **Prompt Input**  
   You type something like:
   ```
   Create a folder Test on the Desktop.
   ```
2. **LLM Interpretation**  
   The assistant transforms this into an XML instruction:
   ```xml
   <orchestrator version="1.0">
     <action name="create_folder">
       <path>C:\Users\jerom\OneDrive\Bureau\Test</path>
       <make_parents>true</make_parents>
       <if_exists>skip</if_exists>
       <encoding>utf-8</encoding>
       <correlation_id>...</correlation_id>
       <notes>Idempotent folder creation.</notes>
     </action>
   </orchestrator>
   ```
3. **Execution**  
   Python code parses the XML, applies safety checks, and executes the action locally.

---

## 🎥 Demo

![demo](screenshot/demo.gif)  
*The agent creates a folder from a prompt, then creates a text file inside with a custom message.*

---

## 💡 Why This Matters

This project is a **proof of concept** for **prompt-driven operating systems**:  
- In the future, **OS control may be conversational** — from file management to system configuration, entirely via natural language.
- AI agents could act as secure interpreters between human intent and system commands.
- This approach reduces the need for repetitive UI navigation, enabling faster, more intuitive workflows.

---

## 🛠️ Requirements

- Python 3.9+
- Packages:  
  ```bash
  pip install openai langchain-openai gradio python-dotenv
  ```
- An OpenAI API key stored in `ENV/env.txt`:
  ```
  OPENAI_API_KEY=sk-...
  ```

---

## ▶️ How to Run

1. Clone the repository.
2. Place your API key in `ENV/env.txt`.
3. Open one of the notebooks:
   - `code/HelloWorld_AI_Agent.ipynb` for the basic Python version.
   - `code/AI_Agent_Langchain.ipynb` for the LangChain modular version.
4. Run all cells and launch the Gradio UI.
5. Start prompting your agent!

---

## 📜 License

MIT License — free to use and adapt.
