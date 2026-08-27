# 🏷️ Autonomous GitHub Issue Analyzer

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangGraph-Powered-green?style=for-the-badge)](https://langchain.com/)
[![GitHub API](https://img.shields.io/badge/GitHub-API-black?style=for-the-badge&logo=github)](https://docs.github.com/en/rest)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

**An intelligent agent that automatically analyzes, categorizes, and scores GitHub issues using Large Language Models.**

</div>

---

## 📖 Overview

The **Autonomous GitHub Issue Analyzer** is an AI agent designed to streamline open-source and enterprise software maintenance. By fetching issues directly from GitHub or accepting text input, it performs deep semantic analysis to determine severity, category, priority, and required expertise. 

This project showcases the integration of external APIs with LLM processing and structured data extraction, providing immediate, actionable insights for maintainers.

## ✨ Features

- **🔍 Direct GitHub Integration**: Fetch and analyze real issues instantly by providing a GitHub issue URL.
- **📊 Structured JSON Output**: Extracts structured data including severity (critical/high/medium/low), category (bug/feature/docs/etc.), and a priority score (1-10).
- **👤 Smart Assignee Recommendation**: Determines the appropriate engineering team (e.g., frontend, backend, devops) based on the issue content.
- **✅ Quality Assurance**: Automatically evaluates whether the provided reproduction steps are clear, or if more information is needed from the reporter.
- **📝 Automated Summarization**: Generates a concise, one-sentence summary and provides custom analyzer notes.

## 🚀 Quick Start

### 1. Prerequisites

- Python 3.10 or higher
- OpenAI API Key
- GitHub Personal Access Token (Optional, but recommended for API rate limits)

### 2. Installation

Clone this repository and install the dependencies:

```bash
git clone https://github.com/yourusername/github-issue-analyzer.git
cd github-issue-analyzer
pip install -r requirements.txt
```

### 3. Configuration

Create a `.env` file and add your API keys:

```env
OPENAI_API_KEY=your_openai_api_key
GITHUB_TOKEN=your_github_token_optional
```

### 4. Usage

The agent can process an issue directly via URL or via manual text input.

**Option A: Fetch from GitHub URL (Recommended)**
```bash
python agent.py --issue-url https://github.com/owner/repo/issues/123
```

**Option B: Manual Input**
```bash
python agent.py --title "Login fails on mobile Safari" --body "When I try to login on iOS 16, the button doesn't respond."
```

## 🧠 How It Works

1. **Data Fetching**: The `fetch_github_issue` function interfaces with the GitHub REST API to pull the title, body, and existing labels.
2. **Prompt Engineering**: The agent uses a highly-constrained system prompt (`TRIAGE_PROMPT`) to force the LLM into returning a strictly formatted JSON object.
3. **LLM Processing**: Leverages `gpt-4o-mini` to perform semantic analysis and evaluate the issue against multiple dimensions.
4. **Parsing & Presentation**: The JSON response is parsed safely using regex fallbacks, then presented in a clean, emoji-rich terminal UI.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📜 License

This project is licensed under the MIT License.
