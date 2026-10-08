# Assignment 3 — CodeTrack: Branching Workflow (Add & Verify a Contact Page)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will add a new Contact page to CodeTrack using a clean feature-branch workflow. You will keep each change in a separate commit, prove that your default branch remains unchanged before the merge, and validate the result after merging.

---

# Task 1 — Confirm Repository State and Default Branch

## Goal

Start from a clean default branch (`main` or `master`) and confirm the repository status.

### Evidence

#### Screenshot 1 — Output of `git status` and `git branch` showing a clean status and the default branch checked out

<img width="850" height="178" alt="Screenshot 2026-10-06 200757" src="https://github.com/user-attachments/assets/42a213aa-dde1-47d6-a9d7-5e54081f0cf3" />


---

# Task 2 — Create and Switch to a Feature Branch

## Goal

Create a branch named exactly `feature/contact-page` and switch to it.

### Evidence

#### Screenshot 2 — Output of `git checkout -b feature/contact-page` and `git branch` showing `* feature/contact-page`

<img width="983" height="185" alt="Screenshot 2026-10-06 201008" src="https://github.com/user-attachments/assets/6e47a0f6-e181-4d98-a0ff-fa919b899e52" />

---

# Task 3 — Add contact.html on the Feature Branch

## Goal

Create `contact.html` with the provided content and commit it alone using the message `feat(contact): add Contact page`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `contact.html`

<img width="962" height="260" alt="Screenshot 2026-10-06 201249" src="https://github.com/user-attachments/assets/c7f4abd4-c860-4723-b5d6-749adf65d1ba" />


---

#### Screenshot 4 — Output of `git commit`
<img width="988" height="122" alt="Screenshot 2026-10-06 201654" src="https://github.com/user-attachments/assets/58c15dc6-8d26-42cb-b6d4-ce3cbcee4ebd" />

---

#### Screenshot 5 — Output of `git log --oneline -3` showing the new commit
<img width="986" height="131" alt="Screenshot 2026-10-06 201824" src="https://github.com/user-attachments/assets/5339c01f-2a74-4a25-afaa-868d952d3dc9" />


---

# Task 4 — Add the Contact Link to index.html

## Goal

Add the provided Contact Page link to `index.html` and commit it separately using the message `feat(nav): add Contact Page link`.

### Evidence

#### Screenshot 6 — Output of `git status` showing `index.html` as modified before staging

<img width="971" height="215" alt="Screenshot 2026-10-08 202303" src="https://github.com/user-attachments/assets/5791ee18-5cc9-44f4-8435-3d94b8d1fcd3" />


---

#### Screenshot 7 — Output of `git commit`

<img width="960" height="318" alt="Screenshot 2026-10-08 201824" src="https://github.com/user-attachments/assets/37f23722-a2f1-4e36-9e58-9c34b0e04093" />

---

#### Screenshot 8 — Browser showing the Contact Page link on the homepage while on `feature/contact-page`

Add your screenshot here.

---

# Task 5 — Verify Isolation (Prove the Default Branch Is Unchanged)

## Goal

Switch back to the default branch and confirm that `contact.html` and the Contact Page link do not exist there yet.

### Evidence

#### Screenshot 9 — Terminal showing the checkout and `ls` output, proving `contact.html` is absent

<img width="937" height="150" alt="Screenshot 2026-10-08 204944" src="https://github.com/user-attachments/assets/b499656d-009c-4b68-a658-c4ddebe70a7e" />


---

#### Screenshot 10 — Browser showing the homepage on the default branch with no Contact Page link

Add your screenshot here.

---

# Task 6 — Merge the Feature Branch into the Default Branch

## Goal

Merge `feature/contact-page` into your default branch and confirm the Contact page works.

### Evidence

#### Screenshot 11 — Output of `git merge feature/contact-page`

<img width="957" height="73" alt="Screenshot 2026-10-08 205150" src="https://github.com/user-attachments/assets/a4214462-c787-4c57-ab09-0adc6c838553" />

---

#### Screenshot 12 — Output of `ls` showing `contact.html` after the merge

<img width="942" height="83" alt="Screenshot 2026-10-08 205254" src="https://github.com/user-attachments/assets/cafde8e6-bfbb-43f6-9793-be0d39bd49af" />


---

#### Screenshot 13 — Browser showing the Contact page opened from the homepage link on the default branch

Add your screenshot here.

---

# Task 7 — Inspect History (Graph View)

## Goal

Display the repository history as a graph and locate both feature commits.

### Evidence

#### Screenshot 14 — Full output of `git log --oneline --graph --decorate --all`

<img width="1001" height="240" alt="Screenshot 2026-10-08 205432" src="https://github.com/user-attachments/assets/73600056-e924-46a3-b559-a7914ffca559" />

---

# Task 8 — Optional Cleanup (Delete the Feature Branch)

## Goal

Delete the merged `feature/contact-page` branch to keep your branch list clean.

### Evidence

#### Screenshot 15 (Optional) — Output showing `feature/contact-page` deleted and no longer listed

<img width="1247" height="202" alt="Screenshot 2026-10-08 205735" src="https://github.com/user-attachments/assets/9a476406-cd9d-44d5-b4da-2540c43ec95f" />


---

# Submission Instructions

- Tasks 1–7 are required; Task 8 is optional
- Add all required screenshots in your submission
- Evidence must show `contact.html` and the homepage link were absent before merging, and working after merging
- Do not expose passwords, access tokens, or private keys

---

# Completion Checklist

- [✅] Repository confirmed clean on the default branch (Screenshot 1)
- [✅] `feature/contact-page` created and checked out (Screenshot 2)
- [✅] `contact.html` added in its own commit (Screenshots 3–5)
- [✅] Homepage Contact link added in a separate commit (Screenshots 6–8)
- [✅] Default branch proven unchanged before merge (Screenshots 9–10)
- [✅] Feature branch merged and Contact page verified (Screenshots 11–13)
- [✅] Graph history reviewed (Screenshot 14)
- [✅] Optional cleanup completed (Screenshot 15)
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
