# 🧪 Sndbx – CLI-First Rust Sandbox Engine

**Sndbx** is a fast, secure sandbox engine built in Rust. Designed to run as a command-line tool, it executes untrusted or suspicious files in a tightly controlled environment, collecting behavioral signals for analysis. Ideal for use in automation pipelines, AV tools, or file-processing engines.

---

## ⚙️ Features

- 🦀 Written in Rust — memory-safe, fast, and robust
- 🖥️ CLI-first interface: run samples with a single command
- 📁 Monitors file system, process activity, and (optionally) network behavior
- 📄 Outputs structured JSON reports for easy parsing
- 🧩 Designed to integrate with other engines (Typrr, Xtrakt, Komprss, etc.)
- 🐳 Future-ready for containerized isolation (Docker-based sandboxing)

---

## 🚀 Quick Start

### 📦 Requirements

- Rust (1.74+ recommended)
- Linux/macOS for full monitoring support

### 🔧 Install

Clone and build the project:

```bash
git clone https://github.com/your-org/sndbx.git
cd sndbx
cargo build --release
````

---

## 🧪 Usage

```bash
sndbx --path ./samples/mystery_file.exe
```

### Common options:

| Flag        | Description                          | Default     |
| ----------- | ------------------------------------ | ----------- |
| `--path`    | Path to the input file               | *Required*  |
| `--output`  | Output directory for the report      | `./output/` |
| `--timeout` | Max runtime (in seconds)             | `30`        |
| `--network` | Enable network access in the sandbox | `false`     |
| `--monitor` | Enable behavioral monitoring         | `true`      |
| `--verbose` | Print detailed logs                  | `false`     |

### Example

```bash
sndbx --path ./samples/dropper.exe --output ./reports --timeout 45 --network
```

---

## 📄 Output

Each run generates a JSON report like this:

```json
{
  "sha256": "abc123...",
  "processes": ["dropper.exe", "powershell.exe"],
  "file_writes": ["/tmp/tmp1234.bat"],
  "network": ["http://suspicious.domain"],
  "tags": ["downloads_file", "suspicious_behavior"]
}
```

---

## 📚 Roadmap

* [x] CLI interface
* [ ] Docker-based sandbox mode
* [ ] File system snapshot diffing
* [ ] eBPF or syscall monitoring (Linux)
* [ ] YARA and AV signature support
* [ ] Report scoring/tagging engine
* [ ] Web API (optional)

---

## 🛡️ Security

* Files executed with timeout and isolation
* No network access by default
* Optional Docker-based runtime in development
* Runs as non-root where possible

---

## 🤝 Contributing

Pull requests, issues, and feature suggestions are welcome!

1. Fork the repo
2. Create a feature branch
3. Open a pull request

---

## 📜 License

MIT License © 2025 Your Name or Organization
