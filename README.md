# AI Business Advisor Workflow

A LangChain notebook that turns an industry into a business idea, evaluates its strengths and weaknesses, and produces a structured report.

## Content

- Prompt templates and LCEL runnable composition
- DuckDuckGo market searches with source IDs, URLs, and excerpts
- Risk classification with `RunnableBranch`: HIGH-risk ideas receive conservative due diligence; STANDARD-risk ideas use the regular analysis
- A structured report that distinguishes source-backed signals from assumptions
- Three validation experiments with measurable success criteria
- Optional in-memory conversation history by session

- ADD A tool in this!!

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
python -m pip install langchain-openai ddgs grandalf ipykernel
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

The workflow makes OpenAI API calls, which may incur usage charges. Market research uses DuckDuckGo search results; snippets can be stale or inaccurate, so review the cited pages before relying on a claim. If search fails, treat market claims as assumptions. The ASCII graph display uses `grandalf`; the notebook prints an installation hint if it is unavailable.

## Memory Demo

The session-memory cells demonstrate `RunnableWithMessageHistory` with in-memory history. Conversation history is kept only for the current Python process and is not persisted after the kernel stops.
