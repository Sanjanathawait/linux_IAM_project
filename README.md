# Linux IAM & System Hardening — Mini Project
## Author: Sanjana Thawait (ERP: 6604710)
### B.Tech CSE (Cybersecurity), Semester 5, Section CY5A
---

## ✅ Project Objective
Design and implement a secure user/group and permission model on an Ubuntu Virtual Machine,
introduce intentional misconfigurations, attack using Kali Linux, fix vulnerabilities,
and produce audit-based remediation proof.

---

## 🛠️ Tools / Environment
| Component | Purpose |
|----------|----------|
| **Ubuntu VM** | Target machine (users, groups, sudo, ACL, auditd) |
| **Kali Linux VM** | Attacker machine (SSH, Nmap, privilege escalation) |
| **auditd** | Tracks changes to critical files (sudoers, passwd) |
| **ACL + POSIX permissions** | Fine‑grained folder access control |
| **SSH + Nmap** | Remote exploitation and scanning |

---

## 📌 Tasks Performed

### ✅ Task 1 — Secure Baseline Setup
1. Created users and groups (admin, devs, auditors)
2. Applied least privilege using `/etc/sudoers.d/*`
3. Configured ACL on `/srv/project`
4. Enabled `auditd` logging for sudoers & passwd changes

---

### ✅ Task 2 — Vulnerable Snapshot + Exploitation + Fix

| Vulnerability | Evidence | Resolution |
|--------------|----------|------------|
| World‑writable cron job | `ls -l /etc/cron.d/backup` | Permission set to `644`, root only |
| Unrestricted sudo (NOPASSWD) | `grep -R NOPASSWD /etc/sudoers*` | Removed entry + validated using `visudo` |
| Weak private key permissions | `ls -l /root/secrets/id_rsa_test` | `chmod 600` to secure key |

✅ Attack was executed from Kali → SSH → escalated to root  
✅ All fixes verified using screenshots and audit logs

---

## 🔍 Evidence Included
- Before & after screenshot proof (cron, sudoers, key permissions)
- Audit logs (`ausearch -k sudoers_change -i`)
- Word + PDF + screenshots

---

## 📂 Submission Contents

```
Linux-IAM-Hardening-Sanjana-6604710
│── README.md
│── Linux_IAM_Report_FINAL.pdf

```


End of README ✅
