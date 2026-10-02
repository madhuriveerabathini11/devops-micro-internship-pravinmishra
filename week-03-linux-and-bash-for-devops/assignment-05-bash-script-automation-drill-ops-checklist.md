# Assignment 5 — Bash Script Automation Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will practice Bash scripting by building a series of small automation scripts covering environment setup, variables, arrays, loops, file conditionals, if-else logic, and functions. These scripts form the foundation of real-world Linux automation used in DevOps, cloud, and production support environments.

---

# Task 1 — Bash Environment & Workspace Setup

## Goal

Verify that Bash is available on your system and create a clean workspace for this assignment.

### Evidence

#### Screenshot 1 — Output of `echo $SHELL` and `bash --version`

<img width="945" height="292" alt="Screenshot 2026-10-02 220545" src="https://github.com/user-attachments/assets/8988a1e9-a15a-431c-8cac-8dd0e4e4ba06" />


---

#### Screenshot 2 — Output of `pwd` and `ls -lah` showing the scripts directory

<img width="862" height="763" alt="Screenshot 2026-10-02 220746" src="https://github.com/user-attachments/assets/6821c2fe-6a53-4060-92b9-7fdee8768e0a" />

---

### Notes

Answer the following in your own words:

**1. What is Bash?**

Bash (Bourne Again Shell) is a command-line interpreter used in Linux to execute commands, run scripts, and automate tasks. It helps users interact with the operating system.

---

**2. What is the difference between shell and Bash?**

A shell is a program that allows users to communicate with an operating system using commands. Bash is one type of shell. Other shells include Zsh, Fish, and Dash. In simple words, shell is the general term, and Bash is a specific type of shell.

---

**3. Why is it important to confirm the Bash version before writing scripts?**

It is important to check the Bash version because some commands and features work only in specific versions. Confirming the version helps us write compatible scripts, avoid errors, and ensure the script runs correctly on the system.

---

# Task 2 — Your First Bash Script

## Goal

Create your first Bash script, make it executable, and run it from the terminal.

### Evidence

#### Screenshot 1 — Content of `first-script.sh`

<img width="1028" height="236" alt="Screenshot 2026-10-02 221334" src="https://github.com/user-attachments/assets/a52ca7b2-bbd2-42b9-af0d-c5fd6865aeec" />

---

#### Screenshot 2 — Output of `./first-script.sh`

<img width="917" height="150" alt="Screenshot 2026-10-02 221438" src="https://github.com/user-attachments/assets/fdef3139-80a2-4d32-b670-ac5e9299980f" />

---

#### Screenshot 3 — Output of `ls -l first-script.sh` showing executable permission

<img width="963" height="101" alt="Screenshot 2026-10-02 221520" src="https://github.com/user-attachments/assets/47476b68-5f96-4a05-a36c-3f048f1e5f32" />


---

### Notes

Answer the following in your own words:

**1. What is the purpose of `#!/bin/bash`?**

The #!/bin/bash line tells the operating system to use the Bash shell to execute the script when we run it directly. It is called a shebang.

---

**2. Why do we use `chmod +x` before running a script?**

We use chmod +x script.sh to give the file execute permission. This allows us to run the script directly using ./script.sh.

---

**3. What is the difference between running a script using `./script.sh` and `bash script.sh`?**

./script.sh: Runs the script directly. The file must have execute permission, and its shebang specifies the interpreter.

bash script.sh: Runs the script through Bash explicitly. The file does not need execute permission because Bash reads the file and executes its commands.

---

# Task 3 — Variables: User Information Script

## Goal

Use variables to store and display user-related information.

### Evidence

#### Screenshot 1 — Content of `user-info.sh`

<img width="983" height="265" alt="Screenshot 2026-10-02 222323" src="https://github.com/user-attachments/assets/25e9df3a-a3df-4ea5-8052-fc286e20e0cb" />

---

#### Screenshot 2 — Output of `./user-info.sh`

<img width="957" height="202" alt="Screenshot 2026-10-02 222632" src="https://github.com/user-attachments/assets/1e9920a3-b8b9-4829-82bb-d514ed1b92bf" />


---

### Notes

Answer the following in your own words:

**1. What is a variable in Bash?**

A variable in Bash is a named place used to store information, such as a name, age, course, or date. We can use the stored value later in our script.

---

**2. Why should we avoid spaces around the `=` sign when creating variables?**

In Bash, we should not use spaces around the = sign because Bash requires the assignment to be written without spaces. Spaces can cause Bash to interpret the statement as a command instead of a variable assignment.

---

**3. How do you access the value stored inside a Bash variable?**

We use the $ symbol followed by the variable name to access its stored value.

---

# Task 4 — Arrays & Loops: Tools Checklist Script

## Goal

Use arrays and loops to print a checklist of tools used in Bash scripting.

### Evidence

#### Screenshot 1 — Content of `tools-checklist.sh`

<img width="746" height="400" alt="Screenshot 2026-10-02 223328" src="https://github.com/user-attachments/assets/dc77939e-3aff-4cd2-8a2a-992864e9e231" />


---

#### Screenshot 2 — Output of `./tools-checklist.sh`

<img width="1032" height="297" alt="Screenshot 2026-10-02 223142" src="https://github.com/user-attachments/assets/354cf59b-5a72-4323-8d37-a8166d1ef404" />

---

### Notes

Answer the following in your own words:

**1. What is an array in Bash?**

An array in Bash is a variable that stores multiple values under one name. For example, we can store tool names like Bash, Linux, Git, and Docker in a single array.

---

**2. Why are arrays useful in scripts?**

Arrays are useful because they allow us to store and manage multiple values together. They make scripts easier to organize and help us process multiple items using loops without writing separate commands for each item.

---

**3. What does `"${tools[@]}"` mean?**

"${tools[@]}" is used to access all the elements stored in the tools array. The double quotes help keep each element as a separate item, even if it contains spaces.

---

**4. What is the purpose of the `for` loop in this script?**

The for loop repeats a set of commands for each item in the array. In this script, it takes each tool name one by one and prints it as part of the checklist.

---

# Task 5 — Loops: Number Counter Script

## Goal

Use loops to repeat a task multiple times.

### Evidence

#### Screenshot 1 — Content of `counter.sh`

Add your screenshot here.

---

#### Screenshot 2 — Output of `./counter.sh`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What is a loop?**

Add your answer here.

---

**2. Why do we use loops in Bash scripting?**

Add your answer here.

---

**3. How many times did the loop run in your script?**

Add your answer here.

---

**4. What would you change if you wanted the loop to run 10 times?**

Add your answer here.

---

# Task 6 — Files & Conditionals: File Validation Script

## Goal

Use file checks and conditionals to verify whether files and directories exist.

### Evidence

#### Screenshot 1 — Output of `ls -lah ../test-folder`

Add your screenshot here.

---

#### Screenshot 2 — Content of `file-check.sh`

Add your screenshot here.

---

#### Screenshot 3 — Output of `./file-check.sh`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What does `-d` check in Bash?**

Add your answer here.

---

**2. What does `-f` check in Bash?**

Add your answer here.

---

**3. Why should file and directory paths be stored in variables?**

Add your answer here.

---

**4. What happens if the file does not exist?**

Add your answer here.

---

# Task 7 — Conditionals: Pass or Retry Script

## Goal

Use if-else conditionals to make decisions based on a variable value.

### Evidence

#### Screenshot 1 — Content of `score-check.sh` with `score=85`

Add your screenshot here.

---

#### Screenshot 2 — Output showing `Result: Pass`

Add your screenshot here.

---

#### Screenshot 3 — Content of `score-check.sh` with `score=55`

Add your screenshot here.

---

#### Screenshot 4 — Output showing `Result: Retry`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What is the purpose of if-else in Bash?**

Add your answer here.

---

**2. What does `-ge` mean?**

Add your answer here.

---

**3. Why should conditions be tested with different values?**

Add your answer here.

---

**4. How can conditionals help in automation scripts?**

Add your answer here.

---

# Task 8 — Functions: Final Bash Automation Script

## Goal

Create a final Bash script using functions to organize reusable code.

### Evidence

#### Screenshot 1 — Content of `final-automation.sh`

Add your screenshot here.

---

#### Screenshot 2 — Output of `./final-automation.sh`

Add your screenshot here.

---

#### Screenshot 3 — Output of `ls -lah` showing all created scripts

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What is a function in Bash?**

Add your answer here.

---

**2. Why are functions useful in scripts?**

Add your answer here.

---

**3. Which functions did you create in this script?**

Add your answer here.

---

**4. How does this final script combine variables, arrays, loops, conditionals, files, and functions?**

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

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- All script files must be created and run successfully
- Required notes must be answered clearly for every task
- Do not expose sensitive information (keys, passwords, credentials)

---

# Completion Checklist

- [ ] Task 1: Environment setup verified, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: First script created, executed, permissions verified (Screenshots 1–3, Notes answered)
- [ ] Task 3: Variables script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 4: Arrays and loops script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 5: Counter loop script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 6: File validation script created and run (Screenshots 1–3, Notes answered)
- [ ] Task 7: Pass/Retry conditional script tested with both values (Screenshots 1–4, Notes answered)
- [ ] Task 8: Final automation script created and run (Screenshots 1–3, Notes answered)
- [ ] All scripts run without errors
- [ ] Full Name visible in all required screenshots
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
