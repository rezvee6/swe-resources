# 🐚 Bash & Shell Scripting – Comprehensive Guide

A complete reference for writing powerful Bash scripts, from basics to advanced techniques.

---

## 🔰 Basics

<details>
<summary><strong>📄 Hello World Script</strong></summary>

```bash
#!/bin/bash
echo "Hello, world!"
```

</details>

<details>
<summary><strong>💡 Variables</strong></summary>

```bash
name="Alice"
echo "Hello, $name"
```

</details>

<details>
<summary><strong>🔄 Conditionals</strong></summary>

```bash
if [ "$age" -ge 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi
```

</details>

<details>
<summary><strong>🔁 Loops</strong></summary>

```bash
# For loop
for i in {1..5}; do
  echo "Number $i"
done

# While loop
count=1
while [ $count -le 5 ]; do
  echo "Count is $count"
  ((count++))
done
```

</details>

---

## 🛠️ Intermediate

<details>
<summary><strong>📥 Read Input</strong></summary>

```bash
read -p "Enter your name: " user
echo "Hello, $user!"
```

</details>

<details>
<summary><strong>📁 File Test Operators</strong></summary>

```bash
if [ -f "file.txt" ]; then
  echo "file exists"
fi
```

</details>

<details>
<summary><strong>📜 Functions</strong></summary>

```bash
greet() {
  echo "Hello, $1!"
}

greet "Alice"
```

</details>

<details>
<summary><strong>📦 Arrays</strong></summary>

```bash
arr=("apple" "banana" "cherry")
echo "${arr[1]}"  # banana

for item in "${arr[@]}"; do
  echo "$item"
done
```

</details>

<details>
<summary><strong>📝 String Manipulation</strong></summary>

```bash
str="Hello World"
echo ${str:0:5}  # Hello
echo ${str/World/Bash}  # Hello Bash
```

</details>

---

## 🧠 Advanced

<details>
<summary><strong>🔧 Command Substitution</strong></summary>

```bash
now=$(date)
echo "Current time: $now"
```

</details>

<details>
<summary><strong>🔃 Looping Over Files</strong></summary>

```bash
for file in *.txt; do
  echo "Found file: $file"
done
```

</details>

<details>
<summary><strong>📤 Redirects</strong></summary>

```bash
command > out.txt    # stdout
command 2> error.txt # stderr
command >> append.txt
```

</details>

<details>
<summary><strong>🔗 Pipes & Chaining</strong></summary>

```bash
cat file.txt | grep "hello" | sort
```

</details>

<details>
<summary><strong>⛓️ Trap and Signals</strong></summary>

```bash
trap "echo 'Script interrupted'; exit" SIGINT

while true; do
  sleep 1
done
```

</details>

<details>
<summary><strong>💣 Debugging</strong></summary>

```bash
bash -x script.sh  # Trace execution
set -e             # Exit on error
```

</details>

<details>
<summary><strong>🧵 Background & Parallel Jobs</strong></summary>

```bash
sleep 5 &  # Run in background
wait       # Wait for all jobs
```

</details>

<details>
<summary><strong>📦 Source Another Script</strong></summary>

```bash
source ./utils.sh
```

</details>

---

## 🌐 CLI Tooling

<details>
<summary><strong>📜 Getopts (Flags & Args)</strong></summary>

```bash
while getopts "u:p:" opt; do
  case $opt in
    u) user="$OPTARG" ;;
    p) pass="$OPTARG" ;;
  esac
done
```

</details>

<details>
<summary><strong>🌍 Curl Usage</strong></summary>

```bash
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://api.example.com
```

</details>

<details>
<summary><strong>🧪 jq for JSON Parsing</strong></summary>

```bash
curl -s https://api.example.com | jq '.data.id'
```

</details>

---

## 📚 Tips & Best Practices

- Always use `#!/bin/bash`
- Quote variables: `"$var"`
- Use `set -euo pipefail` for safety
- Prefer `$(...)` over backticks
- Modularize code into functions

---

## 🧪 Testing and Linting Scripts

<details>
<summary><strong>✅ ShellCheck (Linter)</strong></summary>

```bash
shellcheck script.sh
```

</details>

<details>
<summary><strong>🧪 bats (Test Framework)</strong></summary>

```bash
bats test_script.bats
```

</details>
