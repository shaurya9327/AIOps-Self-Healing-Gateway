# AIOps-Self-Healing-Gateway
# 🦞 Autonomous AIOps SRE Gateway
An AI-driven incident remediation system built with **OpenClaw (Moltbot)** and **Google Gemini Pro**.

## 📖 Overview
This project demonstrates an autonomous "Self-Healing" infrastructure loop. It uses an AI Agent as a middleman between a mobile messaging interface (Telegram) and a Linux server to perform real-time diagnostics and service recovery.

## 🚀 Live Demo
| Incident Remediation (Telegram) | System Logic (Backend) |


## 🛠️ Technical Architecture
* **Engine:** OpenClaw (Moltbot) Gateway running on Ubuntu 24.04.
* **LLM:** ChatGPT 5.2 (Model Context Protocol compliant).
* **Security:** Least-Privilege execution via targeted `sudoers` constraints.
* **Interface:** Encrypted Telegram Bot API for remote SRE operations.

## 🔧 Core "Self-Healing" Logic
The agent is configured with a custom **SRE Skill** that allows it to:
1. Detect service failures (Nginx/Docker).
2. Analyze the last 20 lines of system logs for root cause analysis.
3. Perform a config test (`nginx -t`) before attempting a service restart.
4. Report the final status back to the operator.

## 📜 Installation & Setup
To redeploy this environment, use the provided script in `/scripts/setup-agent.sh` and configure the Sudoers policy:
```bash
root ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart nginx, /usr/bin/systemctl status nginx
