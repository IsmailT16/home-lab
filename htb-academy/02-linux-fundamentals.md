# Hack The Box Academy: Linux Fundamentals

**Platform:** Hack The Box Academy[cite: 2, 4]
**Status:** 🔄 In Progress (36.67% Completed)[cite: 4]
**Focus:** Linux CLI, System Enumeration, File & Package Management, Network Inspection, Web Scraping[cite: 1]

> All practical work performed in a personal isolated lab environment and authorized Hack The Box Academy targets.

---

## Skills Acquired

### Core Competencies

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnubash&logoColor=white)
![Vim](https://img.shields.io/badge/Vim-019733?style=flat&logo=vim&logoColor=white)

| Domain | Skills |
|---|---|
| **Navigation & File Search** | Directory navigation, hidden files, inode inspection, `find` predicates (`name`, `size`, `newermt`, `type`), `which`, `wc` |
| **System & Process Info** | Kernel and OS inspection, environment variables, `dpkg` package queries, `ss` socket analysis, `ps` process inspection |
| **Editing & Redirection** | `vimtutor` workflows, standard streams and redirection (`2>/dev/null`), command piping |
| **Web Enumeration** | Fetching remote source with `curl` from Pwnbox, pattern matching with `grep` and `sed`, deduplication with `sort` |

---

## Module Progress Overview

| Section | Type | Topic | Status |
|---|---|---|---|
| 1 | Theory | Linux Structure[cite: 2] | Completed[cite: 2] |
| 1 | Theory | Linux Distributions[cite: 2] | Completed[cite: 2] |
| 1 | Theory | Introduction to Shell[cite: 2] | Completed[cite: 2] |
| 2 | Theory | Prompt Description[cite: 2] | Completed[cite: 2] |
| 2 | Theory | Getting Help[cite: 2] | Completed[cite: 2] |
| 2 | Interactive | System Information[cite: 2] | Completed[cite: 2] |
| 3 | Interactive | Navigation[cite: 2] | Completed[cite: 2] |
| 3 | Interactive | Working with Files and Directories[cite: 2] | Completed[cite: 2] |
| 3 | Interactive | Editing Files[cite: 2] | Completed[cite: 2] |
| 3 | Interactive | Find Files and Directories[cite: 2] | Completed[cite: 2] |
| 3 | Interactive | File Descriptors and Redirections[cite: 2] | Completed[cite: 2] |

---

## Lab Environment & Target Details

- **Target Hostname:** `nixfund`[cite: 1]
- **Target IP:** `10.129.68.183`[cite: 1]
- **Operating System:** Ubuntu 18.04.5 LTS[cite: 1]
- **Session User:** `htb-student`[cite: 1]

### Connection Command

```bash
ssh htb-student@10.129.68.183
```

---

## System Enumeration, Files & Binaries

### Key Concepts & Findings

- **Inode & File Inspection:** Locating files, checking inodes, and reviewing timestamps in directories such as `/var/backups` and `/usr/share/drirc.d`.
- **Target Config Match:** `00-mesa-defaults.conf` (`/usr/share/drirc.d/00-mesa-defaults.conf`, `27K`, `2020-06-12`) matched size (`25k` to `28k`) and timestamp (`after 2020-03-03`) filters[cite: 1].
- **Extension Counts:** Counting `.bak` and `.log` files across the filesystem with `find` and `wc` while suppressing permission errors (`2>/dev/null`)[cite: 1].
- **Binary Location:** Resolving `/usr/bin/xxd` as the system binary path via `which` and `find`[cite: 1].
- **Editor Basics:** Practicing Vim navigation, editing, search, and quit commands through `vimtutor`[cite: 1].

### Commands Used

```bash
find / -name "*conf*" -size +25k -size -28k -newermt "2020-03-03" 2>/dev/null
ls -lh --time-style=full-iso /usr/share/drirc.d/00-mesa-defaults.conf
find / -name "*.bak" 2>/dev/null | wc -l
find / -type f -name "*.log" 2>/dev/null | wc -l
which xxd
find / -name xxd -type f 2>/dev/null
vimtutor
```

---

## Packages, Listening Services & Processes

### Key Concepts & Findings

- **Installed Packages:** Counting installed packages directly from `dpkg` (`ii` status lines)[cite: 1].
- **Listening IPv4 Services:** Found `7` TCP IPv4 services listening on all interfaces (`0.0.0.0:22`, `0.0.0.0:110`, `0.0.0.0:139`, `0.0.0.0:143`, `0.0.0.0:445`, `0.0.0.0:993`, `0.0.0.0:995`), excluding loopback binds (`127.0.0.1:25`, `127.0.0.1:3306`, `127.0.0.53%lo:53`)[cite: 1].
- **ProFTPd Service User:** Identified `proftpd` as the user running the `proftpd` daemon process[cite: 1].

### Commands Used

```bash
dpkg -l | grep -c "^ii"
dpkg --get-selections | grep -c "[[:space:]]install$"
ss -tlpn4
ss -tlpn4 | grep -c "0.0.0.0:"
ps aux | grep -i proftpd
```

---

## Web Path Filtering with cURL (Pwnbox)

> **Note:** Run from Pwnbox (after exiting the `nixfund` SSH session) using a plain URL without Markdown link syntax[cite: 1].

### Command Used

```bash
curl -sL [https://www.inlanefreight.com](https://www.inlanefreight.com) \
  | grep -oE '(https://(www\.)?inlanefreight\.com)?/[a-zA-Z0-9._/-]*' \
  | sed -E 's|^https://(www\.)?inlanefreight\.com||' \
  | sort -u \
  | wc -l
```

---

## CLI Tool Reference

| Tool | Purpose |
|---|---|
| `find` | Search files and directories by name, size, type, and modification time |
| `dpkg` | Query installed Debian/Ubuntu packages and package states |
| `ss` | Inspect network sockets and listening ports |
| `ps` | View active processes and running user accounts |
| `curl` | Transfer data and fetch web page source from the command line |

---

*[← Back to README](../README.md)*
