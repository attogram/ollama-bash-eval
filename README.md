# Ollama Bash Eval

![Release](https://img.shields.io/github/v/release/attogram/ollama-bash-eval?style=flat)
![License](https://img.shields.io/github/license/attogram/ollama-bash-eval?style=flat)
![Bash ≥3.2](https://img.shields.io/badge/bash-%3E=3.2-blue?style=flat)
![GitHub commit activity](https://img.shields.io/github/commit-activity/t/attogram/ollama-bash-eval?style=flat)
![GitHub stars](https://img.shields.io/github/stars/attogram/ollama-bash-eval?style=flat)
![GitHub watchers](https://img.shields.io/github/watchers/attogram/ollama-bash-eval?style=flat)
![Forks](https://img.shields.io/github/forks/attogram/ollama-bash-eval?style=flat)
![Issues](https://img.shields.io/github/issues/attogram/ollama-bash-eval?style=flat)

The `oe` command uses local LLMs via Ollama to translate your natural language requests into executable shell commands. 

For safety, it always shows you the generated command and asks for your approval before running anything. 

Stop forgetting the right flags for tar or git, just ask!

## Library

`oe` uses a subset of the [Ollama Bash Lib](https://github.com/attogram/ollama-bash-lib) to interact with Ollama.
