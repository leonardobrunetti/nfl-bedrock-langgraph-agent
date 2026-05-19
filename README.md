# NFL Bedrock LangGraph Agent

An NFL data analysis agent built with LangGraph, Amazon Bedrock, and deterministic Pandas tools.

This project started from a simple NFL games dataset and builds toward a more reliable agentic data-analysis system.

Instead of letting the LLM freely write Pandas code for every question, the final design gives the model a set of deterministic Python tools and lets LangGraph orchestrate the workflow.

## Motivation

I built this project to explore how LangGraph can be used to create more structured and reliable agentic workflows.

I am also passionate about the NFL, so working with football data made the project more interesting and concrete for me.

Even though this version focuses on NFL game results, the same approach can be applied to similar sports datasets. If a dataset contains structured information such as teams, games, scores, standings, or player statistics, the same pattern can be reused:

1. prepare the dataset with Pandas
2. define reliable analysis functions
3. expose those functions as tools
4. let an LLM choose the right tool
5. use LangGraph to orchestrate the workflow

This means the architecture is not limited to NFL data. It could also be adapted to other sports such as MLB, NBA, soccer, or hockey.

## Project Goal

The goal of this project is to build an agent that can answer natural-language questions about NFL game results.

Example questions:

- Which teams had the best record?
- Which games had the largest score margin?
- Which games had the highest total score?
- Show all available games for a specific team.

## Tech Stack

- Python
- Pandas
- Jupyter Notebook
- LangChain
- LangGraph
- Amazon Bedrock
- Amazon Nova models

## Repository Structure

```text
nfl-bedrock-langgraph-agent/
├── data/
│   └── games.csv
├── notebooks/
│   └── nfl_agent_walkthrough.ipynb
├── README.md
├── requirements.txt
└── .gitignore

## Why This Architecture?

A generic Pandas agent can be useful, but it may sometimes generate incorrect Python code.

In this project, we use a safer pattern:

1. Prepare the NFL dataset with Pandas.
2. Create deterministic Python functions for common football questions.
3. Convert those functions into LangChain tools.
4. Bind the tools to an Amazon Bedrock model.
5. Use LangGraph to manage the agent workflow.

This makes the system more reliable and easier to debug.

## Current Dataset

The current dataset contains NFL games with columns such as:

- season
- week
- game date
- home team
- visiting team
- home final score
- visitor final score

Additional columns are created during preprocessing:

- winner
- loser
- total points
- score margin
- home win indicator

## Current Features

The agent can currently answer questions about:

- team win-loss records
- largest score margins
- highest scoring games
- games played by a specific team

## Limitations

The current dataset only covers part of the 2022 NFL season, so the agent should only answer based on the available games.

It does not currently include:

- player statistics
- injuries
- betting odds
- full season standings
- live data
- play-by-play data

## Next Steps

Possible improvements:

- Add more NFL datasets
- Add player and team statistics
- Add more deterministic tools
- Move notebook logic into a Python package
- Build a small CLI or web app
- Add tests for the analysis functions

