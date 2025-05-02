# Hack The Box - NextPath Web Challenge

## 🚀 Project Overview

This repository contains our team’s presentation and detailed walkthrough of the **NextPath** web exploitation challenge from [Hack The Box (HTB)](https://www.hackthebox.com/). The challenge falls under the **Web Exploitation** category and required creative use of CRLF injection and path traversal techniques to retrieve a hidden flag file.

## 👥 Team Members

- **Vamshi Krishna Bukka** 
- **Revanth Boddupalli** 
- **Deepthi Gummadi**
- **Hariprasad Bikumandla**

## 📂 Contents

- `hack-the-box-nextpath.pdf`: The final presentation submitted for academic evaluation, covering:
  - Problem understanding
  - API restrictions
  - Exploitation techniques
  - Docker analysis
  - Path traversal strategy
  - Final payload construction
  - Prevention measures

## 🔍 Challenge Summary

- **Target Endpoint:** `/api/team?id=payload`
- **Restrictions Identified:**
  - Parameter `id` must be present and an integer.
  - Path traversal attempts blocked.
  - URL path length limited to 100 characters.
  - `.png` appended to requests automatically.

## 🧪 Exploitation Strategy

- **Technique:** CRLF Injection
- **Bypass Logic:**
  - Injected newline characters (`%0A%0D`) to split and override parameters.
  - Used alternate paths (e.g., `/proc/.../flag.txt`) to locate the hidden flag.
  - Exploited Docker container structure to bypass path constraints.

### Final Payload:
```text
http://<IP>:<PORT>/api/team?id=1%0A%0D&id=../../../../../../../../../../../../../../../../../proc/1/task/1/root/proc/1/root/proc/1/task/1/root/flag.txt
