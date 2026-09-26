# Assignment 4 — Building Your AI Team

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build and configure a set of specialized AI subagents inside your project. You will learn how different models and tool permissions define agent behavior, and you will trigger two real agent delegations to analyze security and cost aspects of your Terraform infrastructure.

---

# Task 1 — Create the Agents Folder and Add Files

## Goal

Create the `.claude/agents/` directory and add all required agent files.

### Evidence

#### Screenshot 1 — VS Code sidebar showing `.claude/agents/` with all 3 files

<img width="422" height="191" alt="Screenshot 2026-09-26 232345" src="https://github.com/user-attachments/assets/c86173a4-01f8-41b3-96f3-3888aa65fb0f" />

---

# Task 2 — Compare the Agent Configurations

## Goal

Analyze the configuration differences between the three agents and demonstrate understanding of model and tool selection.

### Written Answers

#### 1. Why does the cost optimizer use Haiku instead of Sonnet?

The cost optimizer uses Haiku because it is designed for fast and cost-efficient tasks such as analyzing cloud costs and identifying optimization opportunities. These tasks usually do not require the deeper reasoning capabilities of Sonnet. Using Haiku reduces API cost and response time while still providing sufficient performance.

---

#### 2. Why does the security auditor NOT have Write in its tools list?
The security auditor does not have Write access because its purpose is to inspect and report security issues, not modify files. Removing Write permission follows the principle of least privilege and prevents the agent from accidentally changing or damaging project files.

---

#### 3. Why does the tf-writer use `inherit` instead of a specific model?
The tf-writer uses inherit so that it automatically uses the model selected by the parent or main agent. This avoids hard-coding a specific model and allows the agent to work with the current model configuration. It also makes the setup more flexible if the model is changed later. 

---

### Evidence

#### Screenshot 2 — `security-auditor.md` frontmatter showing model and tools configuration

<img width="1323" height="988" alt="Screenshot 2026-09-26 232701" src="https://github.com/user-attachments/assets/6dbf5ab0-4d20-4c6f-b297-3350e8baa7d0" />

---

#### Screenshot 3 — `cost-optimizer.md` frontmatter showing the model and tools configuration
<img width="1350" height="892" alt="Screenshot 2026-09-26 232853" src="https://github.com/user-attachments/assets/474e8cd5-b518-4f39-ba58-e0a2d01aea2d" />


---

# Task 3 — Run the Security Auditor

## Goal

Trigger the security auditor agent and analyze the generated security report for your Terraform infrastructure.

### Evidence

#### Screenshot 4 — The delegation message showing Claude launched the security-auditor

Add your screenshot here.

---

#### Screenshot 5 — Security audit report output

Add your screenshot here.

---

# Task 4 — Run the Cost Optimizer

## Goal

Trigger the cost optimizer agent and review the generated cost optimization report.

### Evidence

#### Screenshot 6 — The full cost optimization report

Add your screenshot here.

---

# Submission Instructions

- Ensure all agent files are committed in `.claude/agents/`
- Complete all written answers in your GitHub Repo
- Push final changes to your forked GitHub repository

---

## GitHub Repository URL

Paste your forked repository URL here:

`Add your URL here`

---

# Completion Checklist

- [ ] `.claude/agents/` folder contains all 3 agent files
- [ ] Screenshot 2 shows correct `security-auditor.md` configuration
- [ ] Screenshot 3 shows correct `cost-optimizer.md` configuration
- [ ] All 3 written answers completed 
- [ ] Security auditor executed successfully
- [ ] Cost optimizer executed successfully
- [ ] Security report is visible with findings
- [ ] Cost report is visible with recommendations
- [ ] All required screenshots added
- [ ] GitHub repo updated with agents

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
