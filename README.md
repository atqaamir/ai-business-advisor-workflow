# AI Business Advisor Workflow

A LangChain notebook that turns an industry into a business idea, evaluates its strengths and weaknesses, and produces a structured report.

## What It Covers

- Prompt templates and LCEL runnable composition
- A logged idea-generation and analysis workflow
- Structured report output using Pydantic
- An end-to-end chain and optional in-memory chat history by session

## Requirements

- Python 3.10 or later
- An OpenAI API key with access to `gpt-4o-mini`
- VS Code with the Jupyter extension, or another Jupyter environment

## Setup

From PowerShell in the project directory:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install langchain-openai grandalf ipykernel
```

Make `OPENAI_API_KEY` available to the notebook kernel before starting it. For example, set it in the PowerShell session that launches VS Code:

```powershell
$env:OPENAI_API_KEY = "your-api-key"
code .
```

Do not commit API keys or other secrets. If VS Code is already running, restart it and the notebook kernel after changing environment variables so the kernel receives the updated value.

## Run

1. Open `ai_business_advisor.ipynb` in VS Code.
2. Select the `.venv` Python kernel.
3. Run the notebook from top to bottom.
4. Change the industry passed to `e2e_chain.invoke(...)` to explore other sectors.

The workflow makes OpenAI API calls, which may incur usage charges. The ASCII graph display uses `grandalf`; the notebook prints an installation hint if it is unavailable.

## Memory Demo

The final cells demonstrate `RunnableWithMessageHistory` with in-memory session history. Conversation history is kept only for the current Python process and is not persisted after the kernel stops.
