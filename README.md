# AI-Assisted EDA Playbook

## Project Goal
- Build a **reusable, AI-assisted Exploratory Data Analysis (EDA) playbook** applicable to any tabular CSV dataset
- Demonstrate a clear human-AI collaboration model: Claude Code handles code generation, you control all decisions
- Produce a portfolio-ready project showing applied AI literacy for your CV
- Practice the full data analysis cycle: profiling → stakeholder framing → answering business questions
- Showcase the ability to critically evaluate and correct AI-generated outputs

## Dataset (Project 1)
**Dutch Retail Sales Index** – monthly time-series index (1960–1995) from Dutch public statistics.
**Stakeholder:** Dutch Retail Category Manager, responsible for long-term trend planning and seasonal inventory strategy.

## How I Used Claude Code as a Co-Pilot
I used Claude Code for all code scaffolding and first-draft explanations. My role was to define the stakeholder context, verify every output, and correct errors — including catching that Claude mishandled the decimal-year timestamp format. Claude accelerated the mechanical 80%; domain judgment and quality control stayed with me throughout.

## Tools Used
- Python 3, pandas, matplotlib
- Claude Code (Anthropic) for code generation and brainstorming
- Git + GitHub for version control and portfolio presentation

## Tech Stack
- Python · pandas · Matplotlib · Claude Code (Anthropic)

## Setup
```bash
pip install -r requirements.txt
jupyter notebook playbook.ipynb
```
