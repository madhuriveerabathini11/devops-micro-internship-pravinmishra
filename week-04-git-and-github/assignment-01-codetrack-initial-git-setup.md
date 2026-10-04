# Assignment 1 — CodeTrack: Initial Git Setup (Local Only)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will set up Git correctly on your local machine before starting the CodeTrack project. You will create a local repository and configure your Git identity at both the repository level (local) and the machine level (global). This assignment is local only — you will not push anything to GitHub yet.

---

# Task 1 — Create the CodeTrack Project and Initialize Git

## Goal

Create a `CodeTrack` project folder and initialize it as a Git repository.

### Evidence

#### Screenshot 1 — Output of `git init` inside `CodeTrack` showing "Initialized empty Git repository"

<img width="1018" height="302" alt="Screenshot 2026-10-03 065748" src="https://github.com/user-attachments/assets/7027baac-f69a-4e38-8c53-075a1f39b240" />


---

#### Screenshot 2 — Output of `ls -a` showing the `.git` folder

<img width="836" height="157" alt="Screenshot 2026-10-03 070043" src="https://github.com/user-attachments/assets/cf44c130-9024-4aed-b758-dc4f2acac6e7" />

---

### Notes

**1. What is the `.git` folder, and why does it matter?**

The .git folder is a hidden folder created when we run git init. It stores important Git information such as commit history, branches, configuration, and tracking data. It matters because it turns the project folder into a Git repository, allowing us to track changes, create commits, and manage the project using Git.

---

# Task 2 — Configure Git Identity Locally (Repository-Only)

## Goal

Set your Git username and email for the `CodeTrack` repository only, using `git config --local`.

### Evidence

#### Screenshot 3 — Output of `git config --local --list` showing your `user.name` and `user.email`

<img width="867" height="600" alt="Screenshot 2026-10-04 145218" src="https://github.com/user-attachments/assets/1fd06e30-bb53-4149-ae87-9bca3e8d7daa" />

---

# Task 3 — Configure Git Identity Globally

## Goal

Set a global Git username and email for this machine using `git config --global`. Note that CodeTrack's local settings still take priority over these.

### Evidence

#### Screenshot 4 — Output of `git config --global --list` showing your `user.name` and `user.email`

<img width="731" height="310" alt="Screenshot 2026-10-04 145507" src="https://github.com/user-attachments/assets/b885c187-b52a-488e-9e5f-82bc33c809b0" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name must be visible in required screenshots
- Do not expose passwords, access tokens, or private keys

---

# Completion Checklist

- [✅] `CodeTrack` folder created and initialized as a Git repository (Screenshots 1–2)
- [✅] Explanation of the `.git` folder written in your own words
- [✅] Local `user.name` and `user.email` configured and verified (Screenshot 3)
- [✅] Global `user.name` and `user.email` configured and verified (Screenshot 4)
- [✅] No sensitive data exposed

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
