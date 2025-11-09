# 📊 AI Financial Researcher

An intelligent multi-agent system that conducts comprehensive financial research and generates professional reports using CrewAI. This project demonstrates advanced AI orchestration with specialized agents working collaboratively to analyze companies and market trends.

## 🌟 Features

- **Multi-Agent Collaboration**: Senior Financial Researcher and Market Analyst agents work together
- **Automated Web Research**: Uses Serper API to gather real-time market data
- **Comprehensive Reports**: Generates professional financial analysis with:
  - Executive summaries
  - Historical performance analysis
  - Market challenges and opportunities
  - Future outlook and projections
- **Structured Output**: Clean, formatted Markdown reports ready for distribution
- **Configurable Agents**: Easy YAML-based configuration for agents and tasks

## 🏗️ Architecture

```
financial_researcher/
├── config/
│   ├── agents.yaml    # Agent definitions (roles, goals, backstories)
│   └── tasks.yaml     # Task definitions and expected outputs
├── tools/
│   └── custom_tool.py # Custom research tools
├── crew.py            # Crew orchestration logic
└── main.py            # Entry point and company selection
```

## 🚀 Quick Start

### Prerequisites

- Python 3.10 - 3.12
- OpenAI API key
- Serper API key (for web search)

### Installation

1. **Clone the repository**
```bash
git clone <your-repo-url>
cd financial_researcher
```

2. **Install dependencies**
```bash
pip install uv
crewai install
```

3. **Configure environment**
```bash
cp .env.example .env
# Edit .env and add your API keys:
# OPENAI_API_KEY=your_key_here
# SERPER_API_KEY=your_key_here
```

### Usage

**Run with default settings (Apple Inc.)**
```bash
crewai run
```

**Customize the company**
Edit `src/financial_researcher/main.py`:
```python
inputs = {
    'company': 'Your Company Name'  # Change this!
}
```

The crew will:
1. 🔍 Research the company using web search
2. 📊 Analyze financial data and trends
3. 📝 Generate a comprehensive report in `output/report.md`

## 📖 Sample Output

The system generates reports with:

- **Executive Summary**: High-level overview of findings
- **Current Status**: Market cap, stock price, revenue metrics
- **Historical Performance**: Multi-year revenue trends and analysis
- **Challenges & Opportunities**: SWOT-style analysis
- **Recent News**: Latest developments and announcements
- **Future Outlook**: Projections and potential developments

[View Sample Report](output/report.md)

## 🛠️ Customization

### Modify Agents

Edit `config/agents.yaml` to customize agent behavior:
```yaml
researcher:
  role: Senior Financial Researcher for {company}
  goal: Conduct thorough research on company {company}
  backstory: >
    You're an expert financial researcher with 20 years of experience...
```

### Modify Tasks

Edit `config/tasks.yaml` to change research objectives:
```yaml
research_task:
  description: >
    Conduct thorough research on company {company}. Focus on:
    1. Current company status
    2. Historical performance
    ...
```

### Add Custom Tools

Create tools in `tools/custom_tool.py`:
```python
from crewai_tools import BaseTool

class MyCustomTool(BaseTool):
    name: str = "My Tool"
    description: str = "What it does"
    
    def _run(self, argument: str) -> str:
        # Your tool logic
        return result
```

## 🔧 Technical Stack

- **CrewAI**: Multi-agent orchestration framework
- **LiteLLM**: Unified LLM interface
- **OpenAI GPT-4**: Language model for analysis
- **Serper API**: Real-time web search
- **Python 3.11**: Core runtime

## 📁 Project Structure

```
financial_researcher/
├── .env.example              # Environment template
├── .gitignore               # Git exclusions
├── pyproject.toml           # Project dependencies
├── README.md                # This file
├── knowledge/               # Knowledge base (optional)
│   └── user_preference.txt
├── output/                  # Generated reports
│   └── report.md
└── src/
    └── financial_researcher/
        ├── __init__.py
        ├── main.py          # Entry point
        ├── crew.py          # Crew definition
        ├── config/          # Configuration files
        │   ├── agents.yaml
        │   └── tasks.yaml
        └── tools/           # Custom tools
            ├── __init__.py
            └── custom_tool.py
```

## 🔐 Security Notes

- Never commit `.env` files with real API keys
- Use `.env.example` as a template
- API keys are loaded via python-dotenv
- The `.gitignore` protects sensitive files

## 🚧 Future Enhancements

- [ ] Add support for multiple companies in one run
- [ ] Integrate financial data APIs (Alpha Vantage, Yahoo Finance)
- [ ] Export reports to PDF format
- [ ] Add visualization of financial trends
- [ ] Support for competitive analysis
- [ ] Email delivery of reports

## 📝 License

MIT License - feel free to use this project for learning and portfolio purposes!

## 🤝 Contributing

Contributions welcome! Please feel free to submit a Pull Request.

## 📧 Contact

Created by [Your Name] - [Your GitHub Profile]

## 🙏 Acknowledgments

- Built with [CrewAI](https://crewai.com)
- Powered by [OpenAI](https://openai.com)
- Search via [Serper](https://serper.dev)

---

**⚠️ Disclaimer**: This tool generates research reports for informational purposes only. Not financial advice. Do not use for trading decisions.
