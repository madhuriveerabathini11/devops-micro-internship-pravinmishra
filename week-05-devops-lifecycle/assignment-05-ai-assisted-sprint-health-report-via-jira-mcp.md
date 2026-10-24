# Assignment 5 — AI-Assisted Sprint Health Report via Jira MCP

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will connect Claude Code to your Jira board through an MCP server, the same way you connected it to GitHub in Week 2, and build a read-only `/sprint-health` skill. The skill reads your current sprint through Jira's API and reports sprint velocity, stories at risk of missing the sprint, and items missing an estimate — but it must never create, edit, comment on, or transition a single ticket itself. You will prove that boundary holds by making a real change on the board yourself and confirming the skill only ever reports, never acts.

---

# Task 1 — Create a Jira API Token

## Goal

Generate an API token from your Atlassian account that the MCP server will use to authenticate with your Jira site. Do not screenshot the token value itself.

### Evidence

#### Screenshot 1 — Jira API token creation confirmation page showing the token name, with the token value not visible

<img width="1077" height="415" alt="Screenshot 2026-10-24 152848" src="https://github.com/user-attachments/assets/6051c439-a767-4565-ab3d-7b8fca74df9e" />


### Notes You Must Write (Very Important):

Why does the MCP server need your site URL and account email in addition to the token?

The site URL tells the server where to connect, the email tells it which account to use, and the API token helps it authenticate securely. All three are needed to establish the Jira connection, and the token must be kept secret.

---

# Task 2 — Create .mcp.json at the Project Root

## Goal

Create or update `.mcp.json` at your project root with a Jira MCP server block, following the same shape as the GitHub MCP server you configured in Week 2.

### Evidence

#### Screenshot 2 — `.mcp.json` open in VS Code showing the Jira server configuration

<img width="1488" height="180" alt="Screenshot 2026-10-24 153106" src="https://github.com/user-attachments/assets/dad2fcea-ef20-4597-8def-b753013796a6" />


### Notes You Must Write (Very Important):

Compare this jira block to the github block from Week 2 Assignment 5. The GitHub server ran via npx (a Node.js package); this one runs via uvx (a Python package) — what stays exactly the same shape despite that difference, and why doesn't Claude Code care which language a given MCP server is written in?

The package runner and implementation language may differ, but the configuration structure and MCP communication protocol remain consistent. This allows Claude Code to use tools built in different programming languages without needing language-specific integration.

---

# Task 3 — Add Your Credentials to settings.local.json

## Goal

Add your Jira site URL, account email, and API token to `.claude/settings.local.json`, and confirm that file is listed in `.gitignore` so it is never committed.

### Evidence

#### Screenshot 3 — `settings.local.json` open in VS Code showing the `env` section, with the actual token value blurred or covered

<img width="783" height="312" alt="Screenshot 2026-10-24 153211" src="https://github.com/user-attachments/assets/dd3928d1-9bf3-406a-988a-6904ddb2217a" />


### Notes You Must Write (Very Important):

Why must JIRA_API_TOKEN live in settings.local.json and never in .mcp.json?

JIRA_API_TOKEN must be stored in settings.local.json and never in .mcp.json because the API token is a sensitive secret.
- settings.local.json: Stores local, private configuration and secrets, helping prevent accidental exposure when the project is shared or committed to Git.
- .mcp.json: Defines the MCP server configuration, such as the server name, command (uvx), arguments, and environment-variable references. It may be committed to Git, so it should not contain actual secret values.
  
---

# Task 4 — Verify the Connection with /mcp

## Goal

Restart Claude Code and confirm the Jira MCP server shows as connected.

### Evidence

#### Screenshot 4 — `/mcp` output showing `jira: connected`

<img width="311" height="117" alt="Screenshot 2026-10-24 154413" src="https://github.com/user-attachments/assets/4c5d26ae-bf7c-47d4-ae85-8c6d30d8ed0f" />


---

# Task 5 — Run a Live Query to Prove Real Board Data

## Goal

Ask Claude to list the issues in your current active sprint through the Jira MCP connection, and confirm the result matches what you see on your live board in the browser.

### Evidence

#### Screenshot 5 — Claude's response showing the live sprint issue list retrieved via Jira MCP

<img width="570" height="577" alt="Screenshot 2026-10-24 204152" src="https://github.com/user-attachments/assets/fd09a60c-9e25-43df-a711-6ef5ec612b9a" />


### Notes You Must Write (Very Important):

How did you confirm this was real board data and not something Claude guessed?

I confirmed it was real Jira board data by checking the information returned directly from the Jira MCP server rather than relying on Claude's generated response.

---

# Task 6 — Build the /sprint-health Skill

## Goal

Create a `/sprint-health` skill restricted to read-only Jira tools plus `Read`, with no issue-mutating tools and no `Write`. Run it and confirm it produces a report covering sprint velocity, at-risk stories, and items missing an estimate.

### Evidence

#### Screenshot 6 — `SKILL.md` frontmatter showing `allowed-tools` limited to read-only Jira tools plus `Read`, with `disable-model-invocation: true`

<img width="1052" height="257" alt="Screenshot 2026-10-24 154100" src="https://github.com/user-attachments/assets/22c4c865-662a-4b6e-a9e9-52e8d385aa79" />


#### Screenshot 7 — `/sprint-health` output showing the full triage report against your real sprint

![Uploading Screenshot 2026-10-24 210702.png…]()



### Notes You Must Write (Very Important):

1. Which Jira MCP tools does this skill's allowed-tools list include, and which mutating tools (create issue, update issue, transition issue, add comment) does it deliberately exclude?

The skill's allowed-tools list includes read-only Jira MCP tools to retrieve board, sprint, issue, and project information. It also includes the Read tool to read files.

It deliberately excludes mutating tools such as create issue, update issue, transition issue, and add comment. This ensures that /sprint-health can inspect sprint data and generate a triage report without making changes to Jira.

2. Why does a Scrum Master need this restriction more than almost any other role in this course?

A Scrum Master must maintain accurate sprint information, protect the team's workflow, and ensure transparency. If an AI agent changes issue statuses, creates issues, or adds comments without approval, it could disrupt sprint tracking and misrepresent the team's progress. Restricting the skill to read-only access allows the Scrum Master to use AI for analysis while keeping all decisions and modifications under human control.

---

# Task 7 — Prove the Skill Never Mutates the Board

## Goal

Manually update one ticket on your board in the browser (for example, move a story to "Done" or add a missing estimate), then run `/sprint-health` again and confirm the new report reflects your change — proving the skill only ever reads live state and never wrote to the board itself.

### Evidence

#### Screenshot 8 — Second `/sprint-health` run showing the report now reflects your manual board change

<img width="578" height="343" alt="Screenshot 2026-10-24 205613" src="https://github.com/user-attachments/assets/8f7de2d8-e37e-42b4-99a5-da00479ef2c0" />

### Notes You Must Write (Very Important):

Map this assignment to Gather → Analyze → Human Act → Verify from Week 3 Assignment 6. Which step did you perform manually in the browser, and why must that step stay human?

Add your answer here

---

# Submission Instructions

Complete all tasks in sequence.

Your submission must include:
- All 8 required screenshots
- All the required notes

---

# Completion Checklist

- [ ] Task 1: Jira API token created, value never screenshotted (Screenshot 1)
- [ ] Task 2: `.mcp.json` has the Jira server block (Screenshot 2)
- [ ] Task 3: Credentials stored in `settings.local.json`, token blurred, file gitignored (Screenshot 3)
- [ ] Task 4: `/mcp` shows the Jira server connected (Screenshot 4)
- [ ] Task 5: Live query returned real sprint data, verified against the browser (Screenshot 5)
- [ ] Task 6: `/sprint-health` skill created with correct read-only `allowed-tools`, and produced a full report (Screenshots 6–7)
- [ ] Task 7: A manual board change was reflected in a second `/sprint-health` run (Screenshot 8)
- [ ] Skill never created, edited, transitioned, or commented on any issue
- [ ] Reflection answered (Notes)
- [ ] No API token value exposed

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
