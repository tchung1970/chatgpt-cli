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

On first run, you will be prompted to enter your first name.<br>
This is saved to `~/.chatgpt-cli.json` and used for the greeting.

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

### Multi-line input

Paste multi-line text (e.g. email headers, code) directly at the `>` prompt — it is automatically detected and displayed as `[Pasted text +N lines]`. You then get a second `>` prompt to type your question before submitting.

You can also use `\` at the end of a line to continue on the next line, or type `/paste` to enter manual multi-line mode (end with `/end`).

### Commands

| Command  | Description           |
|----------|-----------------------|
| `q` / `quit` / `exit` | Quit |
| `/clear` | Reset conversation    |
| `/model` | Show current model    |
| `/paste` | Manual multi-line input mode (end with `/end`) |
| `/help`  | List available commands |
| `\`      | Continue input on next line |

## Configuration

| Environment Variable | Default         | Description          |
|----------------------|-----------------|----------------------|
| `OPENAI_API_KEY`     | *(required)*    | Your OpenAI API key  |
| `CHATGPT_MODEL`     | `gpt-5.4-mini`  | Model to use         |

Environment variables are loaded from `~/.env` at startup.

## License

This project is open source and available under the [MIT License](LICENSE).
