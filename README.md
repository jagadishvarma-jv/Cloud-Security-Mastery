# Cloud Security Mastery Lab Logs

## Lab 1: Linux Process Auditing & Threat Hunting
**Objective:** Identify, investigate, and terminate a malicious background process to ensure system integrity.

### Steps Taken:
1. **Detection:** Used `ps aux` to list all running processes.
2. **Filtering:** Used `grep` to isolate a suspicious `sleep` process acting as a placeholder for a malicious task.
3. **Neutralization:** Executed `kill -9 [PID]` to force-terminate the process immediately.

### Evidence  
! [Detection Phase](detection.png)
! [Neutralization Phase](neutralization.png) 

### Tools Used:
* `ps aux` - Process status (all users)
* `grep` - Pattern matching
* `kill` - Process termination signal

---

## Lab 2: Hardening File Permissions (Least Privilege)
**Objective:** Secure a sensitive file by restricting permissions to "Read-Only" for the owner, preventing unauthorized access or modification.

### Steps Taken:
1. **Creation:** Created a sensitive file `secret.txt` containing confidential data.
2. **Lockdown:** Used `chmod 400` to remove all access from "Group" and "Others," and remove "Write/Execute" access from the owner.
3. **Verification:** Used `ls -l` to audit the file and confirm the hardened permission string: `-r--------`.

### Tools Used:
* `echo` - To create the file and data.
* `chmod 400` - To set absolute permissions (Owner: Read only).
* `ls -l` - To view the file’s security metadata.

### Evidence:
![Hardened Permissions Proof](secured.png)

---

## Lab 3: Network Auditing & Socket Security
**Objective:** Identify active network listeners and analyze the system's "Attack Surface" by auditing open ports.

### Steps Taken:
1. **Network Scan:** Used the `ss -tulpn` command to list all active TCP and UDP listening sockets.
2. **Threat Simulation:** Opened a temporary listener on port `4444` using `nc -l 4444`.
3. **Audit & Cleanup:** Verified the open port in the process list and terminated the listener to return to a secure state.

### Tools Used:
* `ss` - Socket Statistics tool (modern replacement for `netstat`).
* `nc` (Netcat) - Used for reading/writing data across network connections.
* `grep` - To filter specific port numbers from the results.

### Evidence:
![Network Audit Proof](attack.png)
