# Prompt Engineering with the OpenAI API

Interactive Jupyter notebook demonstrating four core prompting techniques using the OpenAI API: **zero-shot**, **few-shot**, **chain-of-thought**, and **system prompting**.

Each technique includes an explanation of what it is, when to use it, and a runnable Python example.

## Techniques Covered

| Technique | Main Idea | Best Used When |
|---|---|---|
| **Zero-shot** | Give an instruction without examples | The task is simple and clearly defined |
| **Few-shot** | Provide labelled examples before the test input | Examples help demonstrate the desired behavior |
| **Chain-of-Thought** | Encourage multi-step reasoning | The problem requires several reasoning or calculation steps |
| **System Prompt** | Establish behavioral rules or constraints | Consistent behavior, role, style, or formatting is required |

### 1. Zero-shot Prompting
Asks the model to perform a task with **no examples** — just an instruction and the input. Demonstrates sentiment classification of a customer review into `Positive`, `Negative`, or `Neutral`.

### 2. Few-shot Prompting
Provides the model with labelled **examples** before the new input. Uses the same sentiment task with three labelled reviews to show the expected input/output pattern.

### 3. Chain-of-Thought Prompting
Encourages step-by-step reasoning for multi-step problems. Demonstrates a multi-step bookstore word problem involving percentages and additions.

### 4. System Prompt
Sets high-level behavioral rules via a system message. Demonstrates an assistant that answers **only in rhyming couplets**.

## Prerequisites

- Python 3.10+
- An [OpenAI API](https://platform.openai.com/) key

## Getting Started

### 1. Clone the repository

```bash
git clone <repo-url>
cd prompt-engineering
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

- **Windows:**
  ```bash
  venv\Scripts\activate
  ```
- **macOS / Linux:**
  ```bash
  source venv/bin/activate
  ```

### 3. Install dependencies

```bash
pip install openai python-dotenv jupyter
```

### 4. Configure your API key

Create a `.env` file in the project root (it is git-ignored):

```
OPENAI_API_KEY=your-api-key-here
```

Optionally, override the default model:

```
OPENAI_MODEL=gpt-4o-mini
```

> **Security:** Never commit your `.env` file or expose your API key. The `.env` file is already listed in `.gitignore`.

### 5. Launch Jupyter Notebook

```bash
jupyter notebook prompt_engineering.ipynb
```

Or with JupyterLab:

```bash
jupyter lab prompt_engineering.ipynb
```

### 6. Run the notebook

Run all cells (Kernel → Restart & Run All). The first code cell initializes the OpenAI client and validates your API key; each subsequent section executes its technique and prints the model's response.

## How It Works

- The notebook loads the API key from `.env` via `python-dotenv` and fails with a clear message if it is missing.
- All requests use the OpenAI **Responses API** (`client.responses.create`) with the default model `gpt-4o-mini`.
- The model name can be changed via the `OPENAI_MODEL` environment variable.
- Every API call is wrapped in a `try/except` block so errors are reported cleanly instead of crashing the notebook.

## Example Output

```text
=== Zero-shot Response ===
Positive
```

```text
=== Few-shot Response ===
Positive
```

```text
=== Chain-of-Thought Response ===
Let's calculate the number of books in stock step by step.
...
Therefore, at the end of Wednesday, the bookstore has **176 books** in stock.
```

## Project Structure

```
prompt-engineering/
├── prompt_engineering.ipynb   # Main notebook with all techniques
├── .env                       # API key configuration (git-ignored)
├── .gitignore                 # Standard Python/Jupyter ignore rules
├── venv/                      # Virtual environment (git-ignored)
└── README.md                  # This file
```

## Key Takeaways

- **Zero-shot** is simple and requires minimal prompt context.
- **Few-shot** demonstrates the expected input/output pattern through examples.
- **Chain-of-thought** is useful for complex, multi-step problems.
- **System prompts** establish higher-level behavioral instructions.
- These techniques can be **combined**: e.g., a system prompt for role, few-shot examples for output format, and a user prompt for the specific task.
