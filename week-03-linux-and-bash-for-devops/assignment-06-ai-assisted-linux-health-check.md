# Assignment 6 — Build an AI-Assisted Linux Health Check (AI-Assisted Linux Incident Triage)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build a read-only Bash triage script that checks the health of your Ubuntu server and Nginx application, connect it to Claude Code as a reusable `/linux-triage` skill, simulate a controlled Nginx incident, use the skill to gather and analyze evidence, recover the service manually, and verify recovery. The workflow follows the Agentic Loop: Gather → Analyze → Human Act → Verify.

---

# Task 1 — Confirm the Healthy Baseline and Create the Workspace

## Goal

Confirm that Nginx and the React application are healthy before building the automation.

### Evidence

#### Screenshot 1 — Output of `systemctl is-active nginx`, `ss -ltn | grep ':80'`, and `curl -I http://localhost`

<img width="1012" height="396" alt="Screenshot 2026-10-03 192501" src="https://github.com/user-attachments/assets/43adca69-29c1-47d9-9049-96dcd383c423" />


---

#### Screenshot 2 — Output of `pwd` and `find . -maxdepth 4 -type d | sort` showing the workspace folder structure

<img width="1042" height="871" alt="Screenshot 2026-10-03 193545" src="https://github.com/user-attachments/assets/c24da451-117f-4f64-a599-d9149c6e8ba7" />

---

### Notes

Answer the following in your own words:

**1. What proves that Nginx is running?**

The command systemctl is-active nginx shows active, which proves that the Nginx service is running.

---

**2. What proves that the server is listening for HTTP traffic?**

The command ss -ltn | grep ':80' shows whether a service is listening on port 80 for HTTP traffic. The command curl -I http://localhost checks whether the local web server responds to an HTTP request.

---

**3. Why must you capture a healthy baseline before simulating an incident?**

Capturing a healthy baseline helps us understand how the server works normally. When an incident occurs, we can compare the new results with the baseline, identify the problem, and verify that the server returns to normal after fixing it.

---

# Task 2 — Create Project Context and Safety Rules in CLAUDE.md

## Goal

Tell Claude exactly what this project does and what it is not allowed to do.

### Evidence

#### Screenshot 3 — CLAUDE.md open in VS Code showing all four sections (Project Overview, Incident Workflow, Safety Rules, Output Rules)
<img width="1132" height="1017" alt="Screenshot 2026-10-03 194743" src="https://github.com/user-attachments/assets/c905e951-965b-405c-92c4-6185978b406a" />


---

### Notes

Answer the following in your own words:

**1. Why should Claude receive project-specific operational rules?**

Claude should receive project-specific rules so it understands the project's purpose, follows the correct workflow, and avoids unsafe changes. These rules help Claude provide relevant and reliable guidance.

---

**2. Why is the human required to execute the recovery command?**

The human must execute the recovery command to maintain control over the system and prevent accidental damage. Before running the command, the human can review its purpose, risks, and expected results.

---

**3. Which rule prevents Claude from making an unsupported diagnosis?**

The rule that requires Claude to use actual evidence, such as command outputs and logs, prevents unsupported diagnoses. Claude should not claim a cause or say a fix succeeded without verification.

---

# Task 3 — Use Agentic AI to Plan Before Writing the Script

## Goal

Use Claude Code to inspect the environment and produce a read-only plan before creating any Bash code.

### Evidence

#### Screenshot 4 — Claude Code showing the five-check plan and read-only inspection results

<img width="1197" height="972" alt="Screenshot 2026-10-04 082231" src="https://github.com/user-attachments/assets/f701f3a6-fcb3-4153-865b-325a163a6bd2" />
<img width="1075" height="927" alt="Screenshot 2026-10-04 082414" src="https://github.com/user-attachments/assets/9ab333d3-4317-47a0-9dbf-8f268f3a1e1f" />


---

### Notes

Answer the following in your own words:

**1. Which part of this task represents the Gather phase?**

The Gather phase is when Claude Code collects information about the project and environment using read-only commands such as pwd, ls -la, bash --version, and git status. This helps understand the current environment before planning the script.

---

**2. Did Claude follow the instruction not to create files? How did you verify this?**

Yes, Claude followed the instruction and did not create or modify any files. I verified this by checking the project directory and using git status to see whether any files had changed.

---

**3. Why is planning before coding useful in DevOps automation?**

Planning before coding helps us understand the environment, identify possible problems, and choose the correct commands. It reduces errors, prevents unwanted changes, and makes automation safer, more reliable, and easier to maintain.

---

# Task 4 — Build the Linux Triage Bash Script

## Goal

Create one Bash script that gathers consistent Linux and Nginx health evidence.

### Evidence

#### Screenshot 5 — Top section of `linux-triage.sh` showing variables, thresholds, and the checks array

<img width="900" height="971" alt="Screenshot 2026-10-04 082900" src="https://github.com/user-attachments/assets/89703ef3-8776-4b8a-90db-e17d571ece2c" />

---

#### Screenshot 6 — Middle section showing check functions and conditionals

<img width="921" height="972" alt="Screenshot 2026-10-04 083344" src="https://github.com/user-attachments/assets/1a1df36d-58fe-4b3d-b086-a177165a58b6" />

---

#### Screenshot 7 — Bottom section showing the loop, summary function, and exit behavior



<img width="931" height="972" alt="Screenshot 2026-10-04 083753" src="https://github.com/user-attachments/assets/983bc835-a4f4-404e-b630-cba982cc662a" />


---

#### Screenshot 8 — Output of `bash -n scripts/linux-triage.sh` (no syntax errors) and `ls -l scripts/linux-triage.sh` showing executable permission

<img width="840" height="150" alt="Screenshot 2026-10-04 110149" src="https://github.com/user-attachments/assets/ccc9f9dc-3a37-482a-8874-605f12e51461" />


---

### Notes

Answer the following in your own words:

**1. What is stored in the checks array?**

The checks array stores the names of the health-check functions that are used to check the server's status.

---

**2. How does the `for` loop use that array?**

The for loop goes through each function name in the checks array one by one and runs the health checks to identify any problems.

---

**3. Why are the health checks separated into functions?**

The health checks are separated into functions to make the script easier to read, understand, test, and maintain. Each function checks a specific part of the server, making it easier to find and fix problems.

---

**4. What is the purpose of `$(...)` in this script?**

The $(...) syntax is called command substitution. It runs a command and stores its output so that the script can use that result in a variable or another command.

---

**5. Why does the script use different exit codes for HEALTHY, WARN, and FAIL?**

The script uses different exit codes to show the server's health status clearly. HEALTHY means everything is working correctly, WARN means there may be a problem that needs attention, and FAIL means a serious problem was found. These codes help users and automation tools understand the result and decide what action to take.

---

# Task 5 — Run and Understand the Healthy-State Report

## Goal

Run the Bash script against the healthy server and verify that it creates a report.

### Evidence

#### Screenshot 9 — Output of `./scripts/linux-triage.sh` showing your Full Name and all five check results

<img width="467" height="523" alt="Screenshot 2026-10-04 111100" src="https://github.com/user-attachments/assets/94499714-2dc7-4579-9a0d-5ead57a71268" />


---

#### Screenshot 10 — Output showing the captured exit code and final summary

<img width="717" height="263" alt="Screenshot 2026-10-04 111311" src="https://github.com/user-attachments/assets/40623046-ff2a-45b2-8144-cfb3935e3e67" />


---

### Notes

Answer the following in your own words:

**1. What is the overall status of your healthy baseline?**

My healthy baseline status is HEALTHY because the server and its required services are running correctly, and no major issues were found during the health checks.

---

**2. Which exact Linux evidence proves the application is serving traffic?**

The output of curl http://localhost shows that the application is responding to HTTP requests. The sudo ss -tulnp command can also show whether the application is listening on its required port.

---

**3. Did your script return exit code 0 or 1? Explain why.**

My script returned exit code 0 because all the health checks passed and the server was healthy. Exit code 0 indicates success, while a non-zero exit code indicates a warning, failure, or another issue depending on how the script is designed.

---

**4. What is the difference between a warning and a failure in this script?**
A warning (WARN) means a potential problem was found that needs attention, but the server may still be working. A failure (FAIL) means a serious problem was detected, such as a required service being stopped or the application not responding. Warnings help us identify issues early, while failures indicate that corrective action may be needed immediately.

---

# Task 6 — Create and Run the /linux-triage Skill

## Goal

Turn the Bash script into a reusable, manually invoked Agentic AI workflow.

### Evidence

#### Screenshot 11 — `SKILL.md` showing the frontmatter, allowed tool restrictions, and safety rules

<img width="865" height="796" alt="Screenshot 2026-10-04 112133" src="https://github.com/user-attachments/assets/3db59bef-0365-40d6-9252-7e197afd6448" />

---

#### Screenshot 12 — `/linux-triage` output for the healthy server

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Why does this skill have Bash, Read, and Grep, but not Write?**

Add your answer here.

---

**2. Why is `disable-model-invocation: true` useful for this skill?**

Add your answer here.

---

**3. What part is performed by Bash, and what part is performed by Claude?**

Add your answer here.

---

**4. Why is this better than asking Claude "Is my server healthy?" without giving it evidence?**

Add your answer here.

---

# Task 7 — Simulate an Nginx Incident and Let the Skill Diagnose It

## Goal

Create a controlled service failure, gather evidence through Bash, and let Claude analyze the evidence without taking recovery action.

### Evidence

#### Screenshot 13 — Output showing Nginx is inactive and the HTTP request fails

Add your screenshot here.

---

#### Screenshot 14 — `/linux-triage` output showing failed evidence, most likely cause, and a suggested recovery command

Add your screenshot here.

---

#### Screenshot 15 — `incident-failure-report.txt` showing the failed checks and your Full Name

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Which three checks failed?**

Add your answer here.

---

**2. What evidence supports the conclusion that Nginx is unavailable?**

Add your answer here.

---

**3. Did Claude execute the recovery command? Why is that important?**

Add your answer here.

---

**4. Which phase of the Agentic Loop is represented by the Bash report?**

Add your answer here.

---

**5. Which phase is represented by Claude's explanation?**

Add your answer here.

---

# Task 8 — Recover Manually, Verify Again, and Write the Incident Summary

## Goal

Recover the service as the human operator and prove that the system is healthy again.

### Evidence

#### Screenshot 16 — Output showing Nginx is active and `curl -I http://localhost` returns 200 OK

Add your screenshot here.

---

#### Screenshot 17 — Second `/linux-triage` output showing successful recovery with no FAIL results

Add your screenshot here.

---

#### Screenshot 18 — Output of `ls -lah reports` showing both `incident-failure-report.txt` and `recovery-report.txt`

Add your screenshot here.

---

#### Screenshot 19 — `incident-summary.md` showing all required sections and your Full Name

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What action did you execute manually?**

Add your answer here.

---

**2. What evidence proves that the service recovered?**

Add your answer here.

---

**3. Why is the second triage run necessary?**

Add your answer here.

---

**4. What could go wrong if an AI agent automatically restarted every failed service?**

Add your answer here.

---

**5. In one sentence, explain the difference between using AI as a chatbot and using AI in this agentic workflow.**

Add your answer here.

---

# Incident Summary

Fill in all seven sections below in your own words.

**Full Name:** Add your full name here

**Date:** DD/MM/YYYY

---

**1. Reported Symptom**

Add your answer here.

---

**2. Evidence Collected**

Add your answer here.

---

**3. Most Likely Cause**

Add your answer here.

---

**4. Human-Approved Recovery Action**

Add your answer here.

---

**5. Verification**

Add your answer here.

---

**6. Safety Decision**

Add your answer here.

---

**7. Agentic Loop Mapping**

Add your answer here.

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — Published LinkedIn post

Add your screenshot here.

---

# GitHub Repository URL

Paste the URL of your GitHub folder or repository containing the assignment files here:

`Add your URL here`

---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name must be visible in required screenshots and the Bash report
- All written answers must be in your own words
- Do not expose sensitive information (keys, passwords, AWS account IDs, tokens)
- GitHub URL must be included in this document

---

# Completion Checklist

- [ ] Task 1: Healthy baseline confirmed, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: CLAUDE.md created with all four sections (Screenshot 3, Notes answered)
- [ ] Task 3: Five-check plan produced by Claude using read-only tools (Screenshot 4, Notes answered)
- [ ] Task 4: `linux-triage.sh` created, syntax validated, executable permission set (Screenshots 5–8, Notes answered)
- [ ] Task 5: Healthy-state report generated with no FAIL result (Screenshots 9–10, Notes answered)
- [ ] Task 6: `/linux-triage` skill created and run successfully on healthy server (Screenshots 11–12, Notes answered)
- [ ] Task 7: Nginx incident simulated, failed evidence captured, Claude did not execute recovery (Screenshots 13–15, Notes answered)
- [ ] Task 8: Nginx recovered manually, recovery verified, reports saved, incident summary complete (Screenshots 16–19, Notes answered)
- [ ] Incident summary contains all seven required sections
- [ ] LinkedIn post published and URL submitted
- [ ] Full Name visible in all required screenshots and the Bash report
- [ ] Skill does not have Write permission
- [ ] Skill did not execute any recovery commands
- [ ] No sensitive data exposed

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
