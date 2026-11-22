# Linux Fundamentals Session Notes and Enumeration

* **Module:** Linux Fundamentals (36.67% completed)[cite: 4]
* **Target:** `nixfund` (`10.129.68.183`), Ubuntu 18.04.5 LTS
* **Session User:** `htb-student`

## File Search and Binary Discovery

### Config File (`25k` to `28k`, after `2020-03-03`)
```bash
find / -name "*conf*" -size +25k -size -28k -newermt "2020-03-03" 2>/dev/null
ls -lh --time-style=full-iso /usr/share/drirc.d/00-mesa-defaults.conf
```
* **Match:** `00-mesa-defaults.conf` (`/usr/share/drirc.d/00-mesa-defaults.conf`, `27K`, `2020-06-12`)

### Counting `.bak` and `.log` Files
```bash
find / -name "*.bak" 2>/dev/null | wc -l
find / -type f -name "*.log" 2>/dev/null | wc -l
```

### Full Path of `xxd`
```bash
which xxd
find / -name xxd -type f 2>/dev/null
```
* **Binary Path:** `/usr/bin/xxd`

## Installed Packages, Listening Services and Processes

### Installed Packages Count
```bash
dpkg -l | grep -c "^ii"
dpkg --get-selections | grep -c "[[:space:]]install$"
```

### Listening IPv4 Services on All Interfaces (`0.0.0.0`)
```bash
ss -tlpn4
ss -tlpn4 | grep -c "0.0.0.0:"
```
* **Count:** `7` services listening on `0.0.0.0` (`22`, `110`, `139`, `143`, `445`, `993`, `995`), excluding localhost (`127.0.0.1:25`, `127.0.0.1:3306`, `127.0.0.53%lo:53`)

### ProFTPd User
```bash
ps aux | grep -i proftpd
```
* **Running User:** `proftpd`

## Web Path Filtering with `curl` (From Pwnbox)
Run from Pwnbox (after exiting `nixfund` SSH) using a plain URL[cite: 1]:
```bash
curl -sL [https://www.inlanefreight.com](https://www.inlanefreight.com) \
  | grep -oE '(https://(www\.)?inlanefreight\.com)?/[a-zA-Z0-9._/-]*' \
  | sed -E 's|^https://(www\.)?inlanefreight\.com||' \
  | sort -u \
  | wc -l
```
