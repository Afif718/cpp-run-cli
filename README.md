# 🚀 cpp-run-cli

A simple Bash utility to compile and run C++ files directly from the terminal using a single command.

---

## 🔧 Setup

1. Open your `.bashrc` (on Linux) or Git Bash's `.bash_profile` (on Windows):

   ```bash
   nano ~/.bashrc
   ```

2. Paste the following into the file:

   ```bash
   runpp() {
     if [ $# -eq 0 ]; then
       echo "❌ Please provide a .cpp file. Example: runpp hello.cpp"
       return 1
     fi

     file="$1"
     if [ ! -f "$file" ]; then
       echo "❌ File '$file' not found."
       return 1
     fi

     tmp_exe="temp_$$.exe"

     g++ "$file" -o "$tmp_exe"
     if [ $? -eq 0 ]; then
       ./"$tmp_exe"
       rm "$tmp_exe"
     else
       echo "❌ Compilation failed."
     fi
   }
   ```

3. Save and reload your shell:

   ```bash
   source ~/.bashrc
   ```

## ▶️ Usage

Navigate to the directory containing your `.cpp` file and run:

```bash
runpp examples/hello.cpp
```

- ✅ Runs if compilation is successful
- ❌ Shows a message if compilation fails

## 💡 Features

- ✅ Minimal command to compile and run C++
- ♻️ Automatically removes the executable after running
- 🛠️ Only shows errors on failure

## 📁 Example Project Structure

```
cpp-run-cli/
├── examples/
│   └── hello.cpp
├── .bashrc-setup
└── README.md
```

## 📌 Requirements

- `g++` compiler installed and available in PATH
- Bash-compatible terminal (Git Bash / WSL / Linux shell)

## 📘 License

MIT License — use it freely and contribute!
