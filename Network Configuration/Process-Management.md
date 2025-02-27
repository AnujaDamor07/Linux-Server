### Process Management in Linux

Process management in Linux is essential for monitoring, controlling, and optimizing the system's performance. Below are the commands and methods used for managing processes, including how to view, manipulate, and monitor running processes.

---

### **Running Commands in Background and Foreground**

1. **Run Command in Foreground:**
   - When you run a command in the foreground, it blocks the terminal until the process finishes.
   - **Example:**
     ```bash
     ping 8.8.8.8
     ```

2. **Run Command in Background:**
   - To run a process in the background, add an `&` at the end of the command.
   - **Example:**
     ```bash
     ping 8.8.8.8 &
     ```

3. **Bring a Job to the Foreground:**
   - If you have a job running in the background, you can bring it to the foreground with the `fg` command.
   - **Example:**
     ```bash
     fg
     ```
   - **Example with Job Number:**
     ```bash
     fg 2
     ```

4. **Send a Large Sequence to `/dev/null` in the Background:**
   - Redirect output to `/dev/null` to discard it, while running in the background.
   - **Example:**
     ```bash
     ping 8.8.8.8 >/dev/null &
     seq 100000000000000000000000 > /dev/null &
     ```

5. **Viewing Background Jobs:**
   - List all jobs running in the background using the `jobs` command.
   - **Example:**
     ```bash
     jobs
     ```

---

### **Viewing Processes with `ps` Command**

1. **Basic Process Status:**
   - View the processes running for the current user.
   - **Example:**
     ```bash
     ps
     ```

2. **Detailed Process Information:**
   - View detailed information about processes (e.g., memory and CPU usage).
   - **Example:**
     ```bash
     ps -l
     ```

3. **List All Processes with CPU and Memory Usage:**
   - Use `ps -aux` to display processes from all users, with their CPU and memory usage.
   - **Example:**
     ```bash
     ps -aux
     ```

4. **List All Processes with Standard Syntax:**
   - Display all processes.
   - **Example:**
     ```bash
     ps -e
     ```

5. **Display Processes in Hierarchical Tree Format:**
   - Use the `ps -axjf` command to show processes in a tree format.
   - **Example:**
     ```bash
     ps -axjf
     ```

6. **Show Processes Owned by Root:**
   - Use `ps` with `-U` option to list processes owned by the root user.
   - **Example:**
     ```bash
     ps -U root -u root u
     ```

7. **Show Processes Owned by a Specific User (e.g., `armour`):**
   - View processes owned by a specific user.
   - **Example:**
     ```bash
     ps -U armour -u armour u
     ```

---

### **Monitoring Processes in Real-Time**

1. **Display Real-Time System Processes:**
   - The `top` command allows you to monitor processes and system resource usage in real-time.
   - **Example:**
     ```bash
     top
     ```

2. **Using `htop` (Better Alternative to `top`):**
   - `htop` provides a more user-friendly, interactive way to monitor processes in real-time.
   - **Install `htop` on Debian/Ubuntu:**
     ```bash
     sudo apt install htop
     ```
   - **Install `htop` on CentOS/RHEL:**
     ```bash
     sudo yum install htop
     ```
   - **Run `htop`:**
     ```bash
     htop
     ```

3. **Show Tree Structure of Processes with `htop`:**
   - Use the `-t` option with `htop` to display processes in a tree structure.
   - **Example:**
     ```bash
     htop -t
     ```

4. **Display Processes for a Specific User (e.g., `armour`) in `htop`:**
   - Filter processes by a specific user.
   - **Example:**
     ```bash
     htop -t -u armour
     ```

5. **Display Details of a Specific Process by PID:**
   - View detailed information about a process by specifying its PID.
   - **Example:**
     ```bash
     htop -t -p 2700
     ```

---

### **Killing Processes**

1. **Send a Termination Signal to a Process by PID:**
   - The `kill` command sends a termination signal to the specified process.
   - **Example:**
     ```bash
     kill 2549
     ```

2. **Forcefully Kill a Process Using SIGKILL:**
   - Use the `-9` option to send a `SIGKILL` signal, forcefully terminating the process.
   - **Example:**
     ```bash
     kill -9 1549
     ```

3. **Kill All Instances of a Process (e.g., `seq`):**
   - Install `psmisc` if necessary, and then kill all instances of a process using `killall`.
   - **Example:**
     ```bash
     sudo yum install psmisc
     killall seq
     ```

4. **Kill All Processes Matching a Name (e.g., `gdm`):**
   - Kill all instances of a process by name.
   - **Example:**
     ```bash
     killall gdm
     ```

5. **Kill All Processes Matching a Name Using Regex (e.g., `firefox`):**
   - Kill processes by using a regex pattern that matches the process name.
   - **Example:**
     ```bash
     killall -r firefox
     ```

6. **Kill All Processes Owned by a Specific User (e.g., `armour`):**
   - Kill all processes owned by a specific user.
   - **Example:**
     ```bash
     killall -u armour
     ```

7. **Kill All Ping Processes Using `pkill`:**
   - Use `pkill` to kill processes by name.
   - **Example:**
     ```bash
     pkill ping
     ```

8. **Kill All Processes for a User (e.g., `armour`) Using `pkill`:**
   - Kill all processes owned by a user with `pkill`.
   - **Example:**
     ```bash
     pkill -u armour
     ```

9. **Kill Exact Match for a Process (e.g., `ping` owned by `armour`):**
   - Kill processes with an exact match of name and user.
   - **Example:**
     ```bash
     pkill -u armour -x ping
     ```

---

### **Summary of Process Management Commands**

| **Command**                             | **Purpose**                                       |
|-----------------------------------------|--------------------------------------------------|
| `jobs`                                  | List background jobs                             |
| `fg`                                    | Bring a job to the foreground                    |
| `ps -aux`                               | View all processes                               |
| `top` / `htop`                          | Monitor system processes in real-time            |
| `kill PID`                              | Terminate a process by PID                       |
| `killall process_name`                  | Kill all instances of a process                  |
| `pkill process_name`                    | Kill a process by name                           |

---

