# Ollama Bash Eval

The `oe` command uses local LLMs via Ollama to translate your natural language requests into executable shell commands. 

For safety, it always shows you the generated command and asks for your approval before running anything. 

Stop forgetting the right flags for tar or git, just ask!

## Library

`oe` uses a subset of the [Ollama Bash Lib](https://github.com/attogram/ollama-bash-lib) to interact with Ollama.
