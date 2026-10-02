# Assignment 3 — Production Maintenance Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will treat your already deployed React application (on Ubuntu VM with Nginx) as a live production system. You will perform structured operational checks covering network validation, service health, log analysis, resource monitoring, configuration verification, and incident simulation with recovery — mirroring real on-call DevOps responsibilities.

---

# Task 1 — Server Access & Networking Validation

## Goal

Verify that the deployed React application is reachable from the browser and confirm basic network connectivity of the Ubuntu VM.

### Evidence

#### Screenshot 1 — Browser showing the React app with your Full Name visible on the UI

<img width="1071" height="762" alt="Screenshot 2026-10-01 232615" src="https://github.com/user-attachments/assets/2c48cfdd-8a41-443b-8082-4de51cff9c00" />


---

#### Screenshot 2 — Output of `ip a`

<img width="1027" height="687" alt="Screenshot 2026-10-01 233011" src="https://github.com/user-attachments/assets/02d0e2a7-20be-495f-9c12-1b064dd83178" />


---

#### Screenshot 3 — Output of `sudo ss -tulpen`

<img width="1060" height="925" alt="Screenshot 2026-10-01 233250" src="https://github.com/user-attachments/assets/b5e3564f-2e15-4e9e-b274-1a5a89f5e83e" />


---

#### Screenshot 4 — Output of `sudo ufw status`

<img width="1041" height="192" alt="Screenshot 2026-10-02 121636" src="https://github.com/user-attachments/assets/03122f82-2f3a-4b91-b9d0-66289e395a8a" />


---

### Notes

Answer the following in your own words:

**1. What proves Nginx is listening on 0.0.0.0:80?**

The output of sudo ss -tulpen shows Nginx listening on 0.0.0.0:80, which means it accepts IPv4 connections on port 80 from any network interface.

---

**2. What proves SSH is active on port 22?**

The output of sudo ss -tulpen shows the SSH service (sshd) listening on port 22. This indicates that the server is ready to accept SSH connections, subject to firewall and network settings.

---

**3. Did you find any unexpected open ports? Explain briefly.**

No, I did not find any unexpected open ports. Only the expected ports for SSH (22) and HTTP (80) were open.

---

# Task 2 — Service Health & Systemd Validation (Nginx)

## Goal

Verify that Nginx is properly installed, running, enabled at boot, and safely configured.

### Evidence

#### Screenshot 1 — Output of `systemctl status nginx --no-pager`

<img width="1036" height="842" alt="Screenshot 2026-10-02 122503" src="https://github.com/user-attachments/assets/1fdf7deb-7c91-484f-a134-b50dc576ef4e" />


---

#### Screenshot 2 — Output of `sudo nginx -t`

<img width="997" height="222" alt="Screenshot 2026-10-02 123054" src="https://github.com/user-attachments/assets/c5057967-9da6-4eaf-8f70-4c327f78276d" />


---

#### Screenshot 3 — Output of `sudo ss -lptn '( sport = :80 )'`

<img width="1010" height="486" alt="Screenshot 2026-10-02 122900" src="https://github.com/user-attachments/assets/0fe3c3e2-a49a-443d-8273-683c508571c3" />

---

### Notes

Answer the following in your own words:

**1. What happens if Nginx fails to restart in production?**

If Nginx fails to restart, the website may become unavailable, and users may not be able to access the application. This can cause service downtime until the issue is fixed.

---

**2. What's your basic rollback plan?**

I will restore the previous working Nginx configuration from a backup, test it using sudo nginx -t, and reload or restart Nginx. Then, I will verify that the website is working correctly.

---

# Task 3 — Logs & Request Trace

## Goal

Verify real traffic flow and analyze logs to understand system behavior and errors.

### Evidence

#### Screenshot 1 — Output of `sudo tail -n 30 /var/log/nginx/access.log`

<img width="1002" height="526" alt="Screenshot 2026-10-02 123923" src="https://github.com/user-attachments/assets/df82b2bd-d8ee-4b9b-bf0e-04136a06ad67" />


---

#### Screenshot 2 — Output of `sudo tail -n 30 /var/log/nginx/error.log`

<img width="1000" height="165" alt="Screenshot 2026-10-02 124116" src="https://github.com/user-attachments/assets/33b696a0-dcab-44aa-bd58-11d126effbd7" />

---

#### Screenshot 3 — Output of `sudo journalctl -u nginx --no-pager -n 50`

<img width="982" height="872" alt="Screenshot 2026-10-02 124237" src="https://github.com/user-attachments/assets/62174d25-1f21-426e-9645-2f6508b10191" />



---

### Notes

Answer the following in your own words:

**1. Were there any errors in the logs?**

- If yes, mention 1–2 example error lines from the logs and explain what each one means in simple terms.
- If no, explain what it means if the error log is empty or shows no recent errors during your check.

No errors were found in the logs during my check. An empty error log or no recent error messages may indicate that Nginx has not encountered any errors that it needed to log during that period.

---

**2. If there were no errors, what does that indicate about the system?**

It indicates that Nginx appears to be running normally without any reported errors during the check. However, further testing is needed to confirm that the website is working correctly.

---

**3. Based on the access logs, were your curl requests visible in the log entries? What does that prove about traffic flow?**

Yes, my curl requests were visible in the Nginx access logs. This proves that HTTP requests reached the Nginx web server and that their responses were recorded in the access log.

---

# Task 4 — System Resource Health Check (Capacity Red Flags)

## Goal

Assess server capacity and detect potential performance or failure risks.

### Evidence

#### Screenshot 1 — Output of `uptime`

<img width="883" height="107" alt="Screenshot 2026-10-02 124907" src="https://github.com/user-attachments/assets/1825b47f-4a42-4787-a4b4-5329d83eebb3" />

---

#### Screenshot 2 — Output of `free -h`

<img width="898" height="146" alt="Screenshot 2026-10-02 125005" src="https://github.com/user-attachments/assets/dfbfa58b-27c0-4348-8d0b-90b940aed9a1" />

---

#### Screenshot 3 — Output of `df -h`

<img width="878" height="506" alt="Screenshot 2026-10-02 125046" src="https://github.com/user-attachments/assets/eb18c889-520f-4ffc-9877-250940c418b4" />

---

#### Screenshot 4 — Output of `sudo du -sh /var/* | sort -h`
<img width="1010" height="427" alt="image" src="https://github.com/user-attachments/assets/f85d4b5d-205c-4a90-ba35-118239253305" />


---

### Notes

Answer the following in your own words:

**1. Which resource looks most critical right now? (CPU/load, memory, or disk) Explain why.**

CPU/load, memory, and disk usage should be checked to identify the most critical resource. If all usage levels are normal, no resource appears critical at the moment.

---

**2. What happens if disk becomes 100% full in a production server?**

If the disk becomes 100% full, the server may fail to write logs, save files, or update data. Applications and services may stop working correctly, and the website may become unavailable. Therefore, disk usage should be monitored regularly and unnecessary files should be removed safely.

---

# Task 5 — Configuration & Deployment Verification

## Goal

Ensure the correct React build is deployed and Nginx is serving it properly.

### Evidence

#### Screenshot 1 — Output of `ls -lah /var/www/html | head -n 20`

<img width="987" height="367" alt="Screenshot 2026-10-02 125421" src="https://github.com/user-attachments/assets/271bde4e-a23f-410e-8844-d41380da54f2" />


---

#### Screenshot 2 — Output of `grep -R "Deployed by" -n /var/www/html 2>/dev/null | head`

<img width="1011" height="931" alt="Screenshot 2026-10-02 125634" src="https://github.com/user-attachments/assets/a420ce3e-fb9c-45fe-bec1-72d7b8c5c865" />


---

#### Screenshot 3 — Output of `grep -n "try_files" /etc/nginx/sites-available/default`

<img width="1000" height="135" alt="Screenshot 2026-10-02 125723" src="https://github.com/user-attachments/assets/0f7b2253-a3dc-4291-a2f2-c6cbaae9b8c2" />

---

### Notes

Answer the following in your own words:

**1. How do you confirm that the correct version of the application is deployed?**




I confirm that the correct version of the application is deployed by checking the application version, verifying the latest code changes, and opening the website in a browser to ensure it displays the expected content and works correctly.



---

# Task 6 — Nginx Configuration Failure Simulation

## Goal

Simulate a real-world Nginx misconfiguration and recover the service safely.

### Evidence

#### Screenshot 1 — Output of `sudo nginx -t` showing the syntax error (broken config)

<img width="997" height="180" alt="Screenshot 2026-10-02 131311" src="https://github.com/user-attachments/assets/ef387116-0fde-498d-8b23-973fffa4abd8" />


---

#### Screenshot 2 — Output of `sudo nginx -t` showing syntax ok (fixed config)

<img width="938" height="61" alt="Screenshot 2026-10-02 131415" src="https://github.com/user-attachments/assets/27b38753-1b74-4d40-bba6-2126057b655c" />

---

#### Screenshot 3 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

<img width="995" height="326" alt="Screenshot 2026-10-02 131921" src="https://github.com/user-attachments/assets/d51334d5-d7da-4b4e-ab11-04ce76e46c56" />


---

### Notes

Answer the following in your own words:

**1. What caused the configuration failure?**

The configuration failed because an invalid directive was added to the Nginx configuration file. Nginx did not recognize the directive, so the nginx -t command showed a syntax error.

---

**2. How did you fix the issue?**

I opened the Nginx configuration file, found the incorrect directive, and removed it. Then I ran sudo nginx -t again to verify the configuration. The test was successful after fixing the error.

---

**3. How can you avoid this kind of issue in real production systems?**

In production systems, we should always test configuration changes before applying them. We can use sudo nginx -t, review changes carefully, keep backups or use version control, and apply changes through a controlled deployment process. This helps prevent configuration errors from affecting the live application.

# Task 7 — Web Application Failure Simulation

## Goal

Simulate missing deployment content and recover the application safely.

### Evidence

#### Screenshot 1 — Output of `curl -I http://<public-ip>` showing failure (non-200 response)

Add your screenshot here.

---

#### Screenshot 2 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What caused the application to break in this scenario?**

Write your answer here

---

**2. How did you fix the issue and restore the application?**

Write your answer here.

---

**3. What steps would you take to prevent this kind of issue in real production systems?**

Write your answer here.

---

# Task 8 — Security & Reliability Review

## Goal

Review and reflect on the security and reliability practices applied during this assignment.

### Security & Reliability Notes

Answer the following in your own words:

**1. Why is SSH key-based authentication more secure than sharing passwords?**

Write your answer here.

---

**2. Why should only required ports be open on a production server?**

Write your answer here.

---

**3. Why is it important for Nginx to be enabled on boot?**

Write your answer here.

---

**4. What are the risks of sharing secrets, keys, or credentials publicly?**

Write your answer here.

---

**5. Why should cloud resources be stopped or terminated when they are no longer needed?**

Write your answer here.

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
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [ ] Task 1: Screenshots (browser, ip a, ss -tulpen, ufw status) + Notes answered
- [ ] Task 2: Screenshots (nginx status, nginx -t, ss port 80) + Notes answered
- [ ] Task 3: Screenshots (access log, error log, journalctl) + Notes answered
- [ ] Task 4: Screenshots (uptime, free -h, df -h, du -sh) + Notes answered
- [ ] Task 5: Screenshots (ls html, grep deployed by, grep try_files) + Notes answered
- [ ] Task 6: Screenshots (nginx -t fail, nginx -t pass, curl recovery) + Notes answered
- [ ] Task 7: Screenshots (curl failure, curl recovery) + Notes answered
- [ ] Task 8: Security & Reliability Notes answered
- [ ] LinkedIn post published and URL submitted
- [ ] Full Name visible in all required screenshots
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
