# 🐚 Ollama Bash Eval (`oe`)

**`oe`** is a minimal AI-powered Bash CLI tool that uses local Ollama models to generate and explain Bash one-liners, or create files like HTML, Markdown, etc.

Built to be:
- POSIX-friendly
- Bash 3.2 compliant
- Shell-native (no config files)
- Model-flexible
- Pipe-friendly

---

## 🧠 Example Usage

```bash
oe find all files over 10GB
oe -x how to show running processes
oe -c make a markdown file about SSH > ssh.md
oe -m llama3 list open ports
oe -m phi3 -x how to tail nginx logs
```

---

## 🧰 Options

| Flag      | Description                                        |
|-----------|----------------------------------------------------|
| `-m`      | Use a specific model and set `OE_MODEL`            |
| `-x`      | Add explanation (as `#` bash-style comment **before** the command) |
| `-c`      | Create a file (e.g. HTML, Markdown, etc)           |
| `-t`      | Provide task as a separate argument                |

---

## 🧠 Model Behavior

- `-m <model>` sets model **for this call** and **updates `OE_MODEL`**
- If `-x` is also used, prints:
  ```bash
  Using model: llama3
  To make this your default: export OE_MODEL=llama3
  ```
- If no `-m`, uses `$OE_MODEL`, or falls back to a random model

---

## 🪄 Example Prompts Used

### 🔹 One-liner generation (`oe`)

> Generate a safe, POSIX-compliant Bash one-liner.
> Task: `{{TASK}}`.
> Return only the command.

---

### 🔹 One-liner with explanation (`oe -x`)

> Generate a safe, POSIX-compliant Bash one-liner.
> Task: `{{TASK}}`.
> Add a short explanation as a Bash comment (`# comment`) **before** the command.
> Output only the comment and command.

---

### 🔹 File creation (`oe -c`)

> Create a plain text file based on this description:
> `{{TASK}}`
> Return only the raw content of the file.
> Do not include explanations or formatting outside the file content.

---

## 🛡️ LLM Output Filtering

- Handles imperfect LLMs (chatty, markdown, etc)
- Strips markdown/code blocks
- Extracts:
  - First valid command
  - First `#` explanation (if `-x` used)
- Ignores intros like:
  - `"Sure! Here's a bash command:"`

---

## 🔄 Persistence

To persist model choice between calls:
```bash
export OE_MODEL=llama3
```

Or let `oe` show you how:
```bash
oe -x -m llama3 "list open ports"
```

---

## ✅ Requirements

- Bash 3.2+
- `curl`
- `jq`
- Local Ollama server running with your model(s)

---

## 🧪 Sample Output

```bash
$ oe -x how to list biggest files

# This lists the 10 largest files and directories in the current folder
du -ah . | sort -rh | head -n 10
```
