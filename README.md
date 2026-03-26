# 📧 Email Refiner Agent

An intelligent multi-agent email refinement pipeline built with **Google ADK**, **LiteLLM**, and **GPT-4o-mini**. Drop in a rough email draft and get back a polished, professional, persuasive version — automatically.

---

## 🧠 How It Works

The pipeline runs five specialized AI agents in loop, each focused on a single dimension of email quality:

```
Your Draft
    │
    ▼
┌─────────────────────┐
│  1. Clarity Editor  │  Removes redundancy, simplifies sentences, eliminates ambiguity
└────────┬────────────┘
         │ clarity_output
         ▼
┌─────────────────────┐
│  2. Tone Stylist    │  Makes the email warm, confident, and human
└────────┬────────────┘
         │ tone_output
         ▼
┌──────────────────────────┐
│  3. Persuasion Strategist│  Strengthens CTA, emphasizes benefits, removes weak language
└────────┬─────────────────┘
         │ persuasion_output
         ▼
┌──────────────────────┐
│  4. Email Synthesizer│  Merges all three versions into one polished final draft
└────────┬─────────────┘
         │ synthesized_output
         ▼
┌──────────────────────┐
│  5. Literary Critic  │◄─── loops up to 3x until approved
│  (LoopAgent)         │     calls escalate_email_complete when ready
└──────────────────────┘
         │
         ▼
    ✅ Final Email
```

---

## 🏗️ Project Structure

```
EMAIL-REFINER-AGENT/
├── email_refiner/
│   ├── __init__.py        # Exposes root_agent for ADK
│   ├── agent.py           # Agent definitions and pipeline orchestration
│   └── prompt.py          # All agent descriptions and instructions
├── .gitignore
├── pyproject.toml
├── uv.lock
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) package manager
- OpenAI API key

### Installation

```bash
# Clone the repo
git clone https://github.com/sajjadanwar0/email-refiner-agent.git
cd email-refiner-agent

# Install dependencies
uv sync
```

### Configuration

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

## 🖥️ Running the Agent

### Browser UI

```bash
adk web
```
---

## 💬 Example Usage

**Input:**
```
hey just wanted to check if you got my last email about the project proposal 
i sent it like a week ago and haven't heard back just let me know what you think thanks
```

**Output (after pipeline):**
```
Subject: Following Up on Project Proposal

Hi [Name],

I wanted to follow up on the project proposal I sent last week.
I'd love to hear your thoughts whenever you have a moment.

Would you be available for a quick call this week to discuss next steps?

Best regards,
[Your Name]
```

---

## 🤖 Agent Details

| Agent | Role | Output Key |
|---|---|---|
| `ClarityEditorAgent` | Removes redundancy, simplifies sentences | `clarity_output` |
| `ToneStylistAgent` | Adjusts warmth, confidence, professionalism | `tone_output` |
| `PersuasionAgent` | Strengthens CTA and persuasive structure | `persuasion_output` |
| `EmailSynthesizerAgent` | Merges all improvements into one draft | `synthesized_output` |
| `LiteraryCriticAgent` | Final quality gate, loops until approved | — |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| [Google ADK](https://github.com/google/adk-python) | Multi-agent orchestration framework |
| [LiteLLM](https://github.com/BerriAI/litellm) | Unified LLM API interface |
| [GPT-4o-mini](https://platform.openai.com/docs/models/gpt-4o-mini) | Underlying language model |
| [uv](https://docs.astral.sh/uv/) | Fast Python package manager |

---
