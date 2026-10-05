# Assignment 2 — CodeTrack: Tracking, Staging, Committing + Deploy to EC2

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will track and stage project files, create two meaningful Git commits in `CodeTrack`, verify your commit history, and deploy the CodeTrack static website to an EC2 instance using Nginx. This connects local version-control practice with a basic manual deployment workflow used in real DevOps environments.

---

# Task 1 — Verify Git Setup and Enter the Repository

## Goal

Confirm that Git works and that you are inside the correct `CodeTrack` repository.

### Evidence

#### Screenshot 1 — Output of `pwd` showing you're inside `CodeTrack`

<img width="851" height="298" alt="Screenshot 2026-10-05 203128" src="https://github.com/user-attachments/assets/ee113c27-28ba-4603-8ce4-4b1f02c0ff96" />


---

#### Screenshot 2 — Output of `git status` showing no "not a git repository" error

<img width="853" height="175" alt="Screenshot 2026-10-05 203315" src="https://github.com/user-attachments/assets/353f91f5-825d-4893-bde6-345da2b2e45e" />


---

# Task 2 — Create index.html and style.css

## Goal

Create the two starter UI files inside `CodeTrack`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `index.html` and `style.css`

<img width="847" height="137" alt="Screenshot 2026-10-05 203622" src="https://github.com/user-attachments/assets/f39c40dc-41b4-491d-bf9f-3e94521093eb" />


---

# Task 3 — Add Starter Content

## Goal

Copy the provided starter HTML and CSS content into your local `index.html` and `style.css` files.

### Evidence

#### Screenshot 4 — Your editor showing the contents of `index.html` and `style.css`

<img width="1307" height="907" alt="Screenshot 2026-10-05 205339" src="https://github.com/user-attachments/assets/3436adc0-56da-4320-b342-0f39f03e9503" />
<img width="1126" height="995" alt="Screenshot 2026-10-05 205502" src="https://github.com/user-attachments/assets/007de364-cfe9-447f-8537-2f06d743158e" />



---

# Task 4 — Track and Stage Files Correctly

## Goal

Confirm both files show as untracked, then stage them individually with `git add`.

### Evidence

#### Screenshot 5 — Output of `git status` showing both files as untracked

<img width="855" height="281" alt="Screenshot 2026-10-05 205756" src="https://github.com/user-attachments/assets/b4d294f6-d24b-4c24-a12f-616675f52c05" />

---

#### Screenshot 6 — Output of `git status` showing both files staged under "Changes to be committed"

<img width="886" height="378" alt="Screenshot 2026-10-05 210028" src="https://github.com/user-attachments/assets/9671620b-6dbb-4adb-9c4d-5dfcededad3a" />

---

# Task 5 — Create the First Commit (Clean Initial Commit)

## Goal

Commit the staged starter files using the message `Initial UI scaffold: add index.html and style.css`, then check the log.

### Evidence

#### Screenshot 7 — Output of `git commit`

<img width="850" height="147" alt="Screenshot 2026-10-05 210222" src="https://github.com/user-attachments/assets/27f1a70f-ae05-40c5-a484-b48c94bc9b3d" />


---

#### Screenshot 8 — Output of `git log --oneline` showing the first commit

<img width="853" height="88" alt="Screenshot 2026-10-05 210554" src="https://github.com/user-attachments/assets/1d1f1f2e-0252-4204-b57b-b67c3ccd1c59" />


---

# Task 6 — Modify index.html and Create a Second Commit

## Goal

Follow the instruction comment inside `index.html` to update the Student Name and Group Name, then commit that change separately using the message `Update homepage content: heading, tagline, CTA button`.

### Evidence

#### Screenshot 9 — Browser showing the updated page with your Student Name and Group Name visible

<img width="835" height="411" alt="Screenshot 2026-10-05 211807" src="https://github.com/user-attachments/assets/8e8587fc-7037-4e7b-9ac6-f6d151b5ed2d" />


---

#### Screenshot 10 — Output of `git status` showing `index.html` as modified

<img width="848" height="218" alt="Screenshot 2026-10-05 212000" src="https://github.com/user-attachments/assets/fba36d5a-8b2a-4b89-8f3a-42795e62edf1" />


---

#### Screenshot 11 — Output of `git commit`

<img width="860" height="175" alt="Screenshot 2026-10-05 212315" src="https://github.com/user-attachments/assets/6fdd17c4-d35f-4220-83eb-33c3d119b9a9" />


---

#### Screenshot 12 — Output of `git log --oneline` showing two commits

<img width="871" height="102" alt="Screenshot 2026-10-05 212443" src="https://github.com/user-attachments/assets/4ba283bb-1a29-47cd-9e07-26467c910a6e" />

---

# Task 7 — Deploy to EC2 with Nginx (Static Website)

## Goal

Install and start Nginx on your EC2 instance, then copy `index.html` and `style.css` into the Nginx web root.

### Evidence

#### Screenshot 13 — Output of `systemctl status nginx --no-pager` showing Nginx `active (running)`

<img width="1187" height="822" alt="Screenshot 2026-10-05 212826" src="https://github.com/user-attachments/assets/f8d61e83-0fbc-4483-b822-17cb85710f09" />


---

#### Screenshot 14 — Output of `curl -I http://localhost` showing `HTTP/1.1 200 OK`

<img width="991" height="236" alt="Screenshot 2026-10-05 212947" src="https://github.com/user-attachments/assets/1ab27429-0cdf-4613-bd2e-32213e5ed424" />

---

#### Screenshot 15 — Browser showing the CodeTrack site loaded at `http://<EC2_PUBLIC_IP>`, with your Full Name and Group Name visible

<img width="835" height="411" alt="Screenshot 2026-10-05 211807" src="https://github.com/user-attachments/assets/8427ebf3-40db-4146-83d2-c9a6ccf19414" />


---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — LinkedIn post showing the deployed CodeTrack application

Add your screenshot here.

---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name and Group Name must be visible in the deployed application evidence
- `git log --oneline` output must show at least two meaningful commits
- Do not expose AWS access keys, passwords, private key contents, or other sensitive information

---

# Completion Checklist

- [ ] `CodeTrack` repository verified with `git status` (Screenshots 1–2)
- [ ] `index.html` and `style.css` created and populated (Screenshots 3–4)
- [ ] Starter files staged and committed in the first commit (Screenshots 5–8)
- [ ] Student Name and Group Name updated in `index.html` (Screenshot 9)
- [ ] Second controlled commit created (Screenshots 10–12)
- [ ] Nginx active on the EC2 instance and CodeTrack reachable via its public IP (Screenshots 13–15)
- [ ] LinkedIn post published and URL submitted
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
