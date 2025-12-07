# 🤖 CodeMentor AI - Intelligent Code Review Assistant

An autonomous AI agent that reviews Python code, detects bugs, and suggests fixes using LangChain and multiple reasoning tools.
---

## ✨ Features

- 🐛 **Bug Detection** - Identifies runtime and logic errors automatically
- 📊 **Code Quality Analysis** - Uses Pylint for style checks
- 🔍 **Solution Search** - Finds fixes on Stack Overflow via Tavily
- 📈 **Complexity Analysis** - Measures code maintainability
- 🤖 **Autonomous Reasoning** - Agent decides which tools to use and when
- 🎨 **Multiple Interfaces** - CLI menu and Gradio web UI

---

## 🚀 Quick Start

### Option 1: Run in Google Colab (Recommended)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sairaiqbal/codementor-ai/blob/main/CodeMentor_AI.ipynb)

1. Click the "Open in Colab" button above
2. Add your API keys to Colab Secrets (🔑 icon in left sidebar):
   - `GROQ_API_KEY` - Get from [console.groq.com](https://console.groq.com)
   - `TAVILY_API_KEY` - Get from [tavily.com](https://tavily.com)
3. Run all cells
4. Use the interactive menu or Gradio UI

### Option 2: Run Locally
```bash
# Download the notebook
wget https://raw.githubusercontent.com/sairaiqbal/codementor-ai/main/CodeMentor_AI.ipynb

# Open in Jupyter
jupyter notebook CodeMentor_AI.ipynb

# Or convert to Python script
jupyter nbconvert --to script CodeMentor_AI.ipynb
python CodeMentor_AI.py
```

---

## 🔑 Setup API Keys

Get **free** API keys:
- **Groq API**: [console.groq.com](https://console.groq.com) (Free tier: 30 requests/min)
- **Tavily API**: [tavily.com](https://tavily.com) (Free tier: 1000 searches/month)

**In Google Colab:**
1. Click 🔑 Secrets in left sidebar
2. Add: `GROQ_API_KEY` and `TAVILY_API_KEY`

**Locally:**
```bash
export GROQ_API_KEY="gsk_your_key_here"
export TAVILY_API_KEY="tvly_your_key_here"
```

---

## 💡 Example Usage

### Interactive Menu
```python
# After running all cells, start the menu
interactive_menu()

# Choose from:
# 1. Review example code (5 pre-loaded buggy examples)
# 2. Review custom code (paste your own)
# 3. Quick debug (describe an error)
# 4. Exit
```

### Direct Code Review
```python
buggy_code = """
def calculate_average(numbers):
    return sum(numbers) / len(numbers)

result = calculate_average([])  # Bug!
"""

review_code(buggy_code)
```

**Agent Output:**
```
============================================================
ITERATION 1
============================================================
Agent: I'll analyze this code step by step...

🔧 Calling tool: analyze_code_quality
📤 Output: No syntax errors found

🔧 Calling tool: execute_python_code
📤 Output: ❌ ZeroDivisionError: division by zero

🔧 Calling tool: search_stackoverflow
📤 Output: Found 2 solutions...

============================================================
FINAL ANSWER
============================================================
Bug: Division by zero when list is empty

Fix:
def calculate_average(numbers):
    if not numbers:
        return 0
    return sum(numbers) / len(numbers)
```

### Quick Debug
```python
quick_debug("How do I fix 'list index out of range' error?")
```

### Gradio UI
```python
# Run this cell to launch web interface
demo.launch(share=True, debug=True)

# Get shareable public link automatically
```

---

## 🛠️ How It Works

The agent uses **ReAct (Reasoning + Acting)** pattern with 4 tools:
```
User Query → Agent Thinks → Chooses Tool → Executes → Analyzes → Repeat → Final Answer
```

**Tools Available:**
1. **`execute_python_code`** - Runs code safely with 5s timeout
2. **`analyze_code_quality`** - Checks style with Pylint
3. **`search_stackoverflow`** - Finds solutions via Tavily
4. **`calculate_complexity`** - Measures cyclomatic complexity

**Example Agent Reasoning:**
```
User: "Review this division function"
  ↓
Agent: "I'll check code quality first"
  ↓
Tool: analyze_code_quality → "No syntax errors"
  ↓
Agent: "Now let me run it"
  ↓
Tool: execute_python_code → "ZeroDivisionError!"
  ↓
Agent: "Let me search for solutions"
  ↓
Tool: search_stackoverflow → "Found 2 solutions"
  ↓
Agent: "Here's the fix with explanation..."
```

---

## 📁 Project Structure
```
codementor-ai/
├── CodeMentor_AI.ipynb    # Main notebook (ALL CODE IN ONE FILE)
├── README.md              # This file
└── LICENSE                # MIT License
```

**The notebook contains:**
- Installation & imports
- API key setup
- Tool definitions (4 tools)
- Agent implementation (ReAct pattern)
- Helper functions
- Interactive menu
- Gradio UI
- Example test cases

---

## 📦 Dependencies

All installed automatically in the notebook:
```bash
pip install langchain-core langchain-groq tavily-python pylint rich gradio
```

**Requirements:**
- `langchain-core>=0.3.0`
- `langchain-groq>=0.2.0`
- `tavily-python>=0.5.0`
- `pylint>=3.0.0`
- `gradio>=4.0.0`
- `rich>=13.0.0`

---

## 🐛 Troubleshooting

**"Model decommissioned" error:**
```python
# Model is updated to: llama-3.3-70b-versatile
# If error persists, check Groq docs for latest model
```

**"API key not found":**
```python
# In Colab: Add keys to Secrets (🔑 icon)
# Locally: Set environment variables
```

**"Tool not executing":**
```python
# Check if all cells are run in order
# Restart runtime and run all cells
```

**Gradio "placeholder not supported":**
```python
# Already fixed in notebook
# gr.Code() doesn't use placeholder parameter
```

---

## 📚 Example Prompts to Try

**Beginner:**
- "Review this code for bugs"
- "Why does this crash?"
- "Find the error in this function"

**Intermediate:**
- "Analyze performance issues"
- "Check code quality and style"
- "Suggest improvements"

**Advanced:**
- "Find security vulnerabilities"
- "Optimize this algorithm"
- "Explain why this is O(n²)"

---

## 🎯 Built With

- **LangChain** - Agent orchestration framework
- **Groq** - Fast LLM inference (Llama 3.3 70B)
- **Tavily** - Web search API
- **Pylint** - Static code analysis
- **Gradio** - Interactive web UI
- **Google Colab** - Cloud notebook environment

---

## 🎓 Educational Value

Perfect for:
- **Students** learning debugging
- **Developers** getting quick code reviews
- **Instructors** teaching best practices
- **Interview prep** for coding challenges

---

## 🎬 Demo

**CLI Interface:**
```
🤖 CODEMENTOR AI - INTERACTIVE MODE

📋 Options:
  1. Review example code (choose from samples)
  2. Review custom code (paste your own)
  3. Quick debug (describe an error)
  4. Exit
```

**Gradio Web UI:**
- Tab 1: Code Review with syntax highlighting
- Tab 2: Quick Debug with error search
- Tab 3: About & Documentation

---

## 🤝 Contributing

This is a single-notebook project, but improvements welcome!

**To contribute:**
1. Fork the repository
2. Make changes to `CodeMentor_AI.ipynb`
3. Test in Google Colab
4. Submit Pull Request with description

**Ideas for contributions:**
- Add more tools (security scanner, test generator)
- Support more languages (JavaScript, Java)
- Improve agent prompts
- Add more example test cases

---

## 📄 License

MIT License - Free to use, modify, and distribute.

---

## 🙏 Acknowledgments

- **LangChain** for agent framework
- **Groq** for free LLM API
- **Tavily** for search capabilities
- **Google Colab** for free GPU/compute

---

## 📧 Contact

**Saira Iqbal**  
GitHub: [@sairaiqbal](https://github.com/sairaiqbal)  
LinkedIn: [(www.linkedin.com/in/saira-iqbal-dev)]

---

## 🚀 Future Enhancements

- [ ] Multi-language support (JS, Java, C++)
- [ ] GitHub integration for PR reviews
- [ ] Unit test generation
- [ ] Code refactoring suggestions
- [ ] VSCode extension
- [ ] Persistent conversation memory

---

⭐ **If this helped you, please star the repository!**

**Live Demo:** [Try it in Colab](https://colab.research.google.com/github/sairaiqbal/codementor-ai/blob/main/CodeMentor_AI.ipynb)
