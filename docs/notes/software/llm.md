# llm CLI tool

- [LLM A CLI utility and Python library for interacting with Large Language Models (llm.datasette.io)](https://llm.datasette.io/en/stable/)
- [Changelog - LLM (llm.datasette.io)](https://llm.datasette.io/en/stable/changelog.html)
- [Prompt templates - LLM (llm.datasette.io)](https://llm.datasette.io/en/stable/templates.html)

## Cool tricks

````shell
```shell
llm prompt "how to restart prometheus as I have updated the config file that is shared to the container: $(<docker-compose.yml)"
````

<iframe width="560" height="315" src="https://www.youtube.com/embed/QUXQNi6jQ30?si=76gokuY2HabmVYde" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Installation

```bash
pipx install llm
llm install llm-cmd llm-anthropic llm-ollama
llm models default claude-3.7-sonnet
```

## Usage

```shell
llm prompt "how to restart prometheus as I have updated the config file that is shared to the container: $(<docker-compose.yml)"
```

```shell
llm models default claude-3.7-sonnet
```

### Natural Language Commands

```shell
 llm cmd "delete all files returned by this command, respecting that some have
spaces in filenames and it's linux: fd Leopold"
> fd Leopold -X rm -f {}
```

### Chat

```shell
# Chat with history
llm chat --history previous_chat.json "your message"
```

## Run a Command

```shell
llm cmd list files in /tmp
> ls /tmp
```

## Embed

```shell
llm embed -m 3-small -c "Hello there"
```

```

```

## List models

```shell
$ llm models
OpenAI Chat: gpt-4-turbo (aliases: gpt-4-turbo-preview, 4-turbo, 4t)
OpenAI Chat: gpt-4o (aliases: 4o)
OpenAI Chat: gpt-4o-mini (aliases: 4o-mini)
OpenAI Chat: o1-preview
OpenAI Chat: o1-mini
OpenAI Completion: gpt-3.5-turbo-instruct (aliases: 3.5-instruct, chatgpt-instruct)
Anthropic Messages: claude-3-opus-20240229 (aliases: claude-3-opus)
Anthropic Messages: claude-3-sonnet-20240229 (aliases: claude-3-sonnet)
Anthropic Messages: claude-3-haiku-20240307 (aliases: claude-3-haiku)
Anthropic Messages: claude-3-5-sonnet-20240620 (aliases: claude-3.5-sonnet)
Ollama: llama3.2:latest (aliases: llama3.2)
Ollama: llama3.1:70b
```
