# 🩺 Linux System Health Check

![Shell Script](https://img.shields.io/badge/Shell-Bash-4EAA25?logo=gnubash&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Linux-FCC624?logo=linux&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

A lightweight Bash script that performs a quick health check of a Linux system and prints a clean, color-coded report in your terminal. No dependencies, no installation, just run it.

---

## 📋 Features

The script collects and displays:

| Section | Details |
|---|---|
| 🖥️ **Hostname & OS** | Machine name and distribution (read from `/etc/os-release`) |
| ⚙️ **Kernel version** | Output of `uname -r` |
| 👤 **Current user** | Username and `id` information |
| 🕒 **Date & time** | Current date, time and timezone |
| 🧠 **Memory usage** | Total, used, free and available RAM/swap |
| 💾 **Disk usage** | Usage per filesystem, plus a grand total |
| ⏱️ **System uptime** | How long the system has been running |

---

## 🚀 Getting Started

### Prerequisites

- A Linux system with **Bash** (4.0+ recommended)
- Standard GNU utilities: `hostname`, `uname`, `whoami`, `date`, `free`, `df`, `uptime` (these come pre-installed on almost every distribution)

### Installation

```bash
# Clone the repository
git clone https://github.com/blacksecopss/linux-health-check.git

# Move into the project folder
cd linux-health-check

# Make the script executable
chmod +x health_check.sh
```

### Usage

```bash
./health_check.sh
```

Or run it without changing permissions:

```bash
bash health_check.sh
```

### Save the report to a file

```bash
./health_check.sh > health_report_$(date +%F).txt
```

> Note: the script uses color codes, so the saved file may contain escape sequences. View it with `less -R` or strip them with `sed 's/\x1b\[[0-9;]*m//g'`.

---

## 📸 Example Output

Your values will differ, this is only an illustration of the layout:

```
=====================================================
           LINUX SYSTEM HEALTH CHECK REPORT
=====================================================
--------------------------------------------------
🔹 Hostname and Operating System
Hostname : my-server
OS       : Ubuntu 24.04 LTS
--------------------------------------------------
🔹 Kernel Version
Kernel   : 6.8.0-generic
--------------------------------------------------
🔹 Current User
User     : alex
...
```

> 💡 Tip: replace this block with a real screenshot of your terminal (e.g. `docs/screenshot.png`) and embed it with `![Screenshot](docs/screenshot.png)`.

---

## 📁 Project Structure

```
linux-health-check/
├── health_check.sh   # Main script
├── README.md         # Project documentation
└── LICENSE           # License file
```

---

## 🧩 How It Works

Each section of the report uses a standard Linux command:

| Information | Command |
|---|---|
| Hostname | `hostname` |
| Operating system | `/etc/os-release` |
| Kernel | `uname -r` |
| Current user | `whoami`, `id` |
| Date and time | `date` |
| Memory | `free -h` |
| Disk | `df -h --total` |
| Uptime | `uptime -p` |

The script checks that `free`, `df` and `uptime` exist before calling them, so it fails gracefully on minimal systems.

---

## 🛣️ Roadmap / Ideas

- [ ] CPU usage and load average
- [ ] Top 5 processes by memory/CPU
- [ ] Warning thresholds (e.g. alert when disk usage > 90%)
- [ ] Network info (IP address, connectivity check)
- [ ] Export report to JSON or HTML
- [ ] Schedule with `cron` and email the report

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push to your branch: `git push origin feature/my-feature`
5. Open a Pull Request

Please keep the script POSIX-friendly where possible and test on at least one major distribution (Ubuntu, Debian, Fedora, etc.). Running [ShellCheck](https://www.shellcheck.net/) on your changes is a great habit.

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**BlackSecOps**
GitHub: [@BlackSecOpss](https://github.com/blacksecopss)
Telegram: [@BlackSecOps](https://t.me/blacksecops)

⭐ If you found this useful, consider giving the repo a star!
