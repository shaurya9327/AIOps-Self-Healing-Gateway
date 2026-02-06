# AIOps-Self-Healing-Gateway
# 🦞 Autonomous AIOps SRE Gateway
An AI-driven incident remediation system built with **OpenClaw (Moltbot)** and **Chat GPT 5.2 (Open AI)**.

## 📖 Overview
This project demonstrates an autonomous "Self-Healing" infrastructure loop. It uses an AI Agent as a middleman between a mobile messaging interface (Telegram) and a Linux server to perform real-time diagnostics and service recovery.

## 🚀 Live Demo
| Incident Remediation (Telegram) | System Logic (Backend) |
![Screenshot 2026-02-05 190641](https://github.com/user-attachments/assets/87d89521-ae97-49f1-bfb9-bc98269d6b6e)
![Screenshot 2026-02-05 190641](https://github.com/user-attachments/assets/87d89521-ae97-49f1-bfb9-bc98269d6b6e)
![Screenshot 2026-02-05 190710](https://github.com/user-attachments/assets/8e7ec7f3-482f-445b-81c2-f3d7125d6ee0)
![Screenshot 2026-02-05 190710](https://github.com/user-attachments/assets/8e7ec7f3-482f-445b-81c2-f3d7125d6ee0)
![Screenshot 2026-02-05 190734](https://github.com/user-attachments/assets/3d78eb95-4766-4652-9758-e549ef6949e3)
![Screenshot 2026-02-05 190734](https://github.com/user-attachments/assets/3d78eb95-4766-4652-9758-e549ef6949e3)
![Screenshot 2026-02-05 190757](https://github.com/user-attachments/assets/93a3323a-8313-41b9-9e04-da3395432038)
![Screenshot 2026-02-05 190757](https://github.com/user-attachments/assets/93a3323a-8313-41b9-9e04-da3395432038)
![Screenshot 2026-02-05 last](https://github.com/user-attachments/assets/887df3a0-be0a-48d9-ac60-b2144d5a3ce3)
![Screenshot 2026-02-05 last](https://github.com/user-attachments/assets/887df3a0-be0a-48d9-ac60-b2144d5a3ce3)
![Screenshot 2026-02-05 190556](https://github.com/user-attachments/assets/d621fc1c-7f1a-43c8-907e-5a2936cfcbf6)
![Screenshot 2026-02-05 190556](https://github.com/user-attachments/assets/d621fc1c-7f1a-43c8-907e-5a2936cfcbf6)


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
