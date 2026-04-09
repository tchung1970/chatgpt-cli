# chatgpt-cli

A lightweight command-line interface for ChatGPT on macOS, powered by the OpenAI Responses API with live web search.

## Features

- Interactive chat with conversation history
- One-shot queries from the command line
- Live web search via OpenAI's `web_search_preview` tool
- Markdown-rendered responses in the terminal
- Configurable model selection

## Requirements

- Python 3.12+
- OpenAI API key

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/tchung/chatgpt-cli.git
   cd chatgpt-cli
   ```

2. Install dependencies:
   ```bash
   pip3 install openai rich
   ```

3. Add your OpenAI API key to `~/.env`:
   ```
   OPENAI_API_KEY=sk-your-key-here
   ```

4. Make the script executable and optionally add it to your PATH:
   ```bash
   chmod +x chatgpt-cli
   ln -sf "$(pwd)/chatgpt-cli" ~/bin/chatgpt
   ```

## Usage

### Interactive mode

```
$ chatgpt
Enter your first name: Thomas
Hi Thomas, How can I help you?
Model: gpt-5.4-mini | Type q to quit

> What's the weather in Los Angeles?
```

### One-shot mode

```
$ chatgpt "What's the weather in Los Angeles?"
```

### Commands

| Command  | Description           |
|----------|-----------------------|
| `q`      | Quit                  |
| `/clear` | Reset conversation    |
| `/model` | Show current model    |
| `/help`  | List available commands |
| `/quit`  | Quit                  |

## Configuration

| Environment Variable | Default         | Description          |
|----------------------|-----------------|----------------------|
| `OPENAI_API_KEY`     | *(required)*    | Your OpenAI API key  |
| `CHATGPT_MODEL`     | `gpt-5.4-mini`  | Model to use         |

Environment variables are loaded from `~/.env` at startup.

On first run, you will be prompted to enter your first name. This is saved to `~/.chatgpt-cli.json` and used for the greeting.

## License

This project is open source and available under the [MIT License](LICENSE).
