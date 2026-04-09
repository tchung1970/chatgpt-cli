# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A single-file Python CLI client for ChatGPT using the OpenAI Responses API with web search enabled. Supports interactive chat with conversation history and one-shot queries.

## Running

```bash
# Interactive mode
./chatgpt-cli

# One-shot query
./chatgpt-cli "your question here"
```

## Dependencies

- Python 3.12+
- `openai` — OpenAI Responses API client
- `rich` — Terminal markdown rendering

Install: `pip3 install -r requirements.txt`

## Configuration

- API key is loaded from `~/.env` (reads `OPENAI_API_KEY`), overriding any inherited env vars
- Model can be overridden via `CHATGPT_MODEL` env var (default: `gpt-5.4-mini`)

## Architecture

Single executable script (`chatgpt-cli`) with no module structure:
- `load_env()` — parses `~/.env`, always overrides existing env vars
- `get_user_name()` — loads or prompts for first name, saved to `~/.chatgpt-cli.json`
- `get_response_text()` — extracts text content from the Responses API output
- `build_input()` — constructs the input array from conversation history
- `chat()` — interactive REPL with readline support, responses rendered as markdown
- `__main__` block — routes between one-shot mode (args present) and interactive mode

Interactive commands: `q`/`quit`/`exit` to quit, `/clear` to reset conversation, `/model` to show model, `/help` for help.

Uses the OpenAI **Responses API** (`client.responses.create`) with `web_search_preview` tool for live internet access.
