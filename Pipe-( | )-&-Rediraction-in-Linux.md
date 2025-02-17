1️⃣ **Pipe (|) in Linux**
🔹 The pipe `(|)` is used to send the output of one command as input to another command. It's a powerful way to chain multiple commands.

📂 Example 1: Using `ls` and `wc -l`

bash
Copy
$ ls | wc -l
📌 This command lists all files and directories in the current directory `(ls)` and then pipes the output to `wc -l` to count the number of lines (i.e., the number of files and directories).

🔍  **Example 2: Filtering Processes Using ps and grep** 

 bash
Copy
$ ps aux | grep firefox
📌 This command lists all running processes `(ps aux)` and filters the results to only show those related to the Firefox process using grep.

2️⃣  **Redirection Operators in Linux**
🔹 Redirection allows you to manage input and output redirection for commands.

📤 **> (Output Redirection – Overwrite)**
 🔄 Redirects the output of a command to a file, replacing the file's contents.

📝 Example: Save ls Output to a File

bash
Copy
$ ls > filelist.txt
📌 This command lists the files and directories in the current directory `(ls)` and saves them to `filelist.txt`, overwriting any existing content in the file.

📤 **>> (Output Redirection – Append)**
🔄 Redirects the output of a command to a file, appending to the file without overwriting the existing content.

📝 Example: Append ls Output to a File

bash
Copy
$ ls >> filelist.txt
📌 This command appends the output of ls to `filelist.txt` without removing the previous content in the file.

📥 **< (Input Redirection)**
🔄 Takes input from a file instead of the keyboard.

📊 Example: Counting Words in a File

bash
Copy
$ wc -l < filelist.txt
📌 This command counts the number of lines in the `filelist.txt` file by redirecting the content of the file to `wc -l`.

⚠️ **2> (Redirecting Error Output)**
🚨 Redirects error messages to a file.

❌ Example: Redirecting Errors to a File

bash
Copy
$ ls /nonexistentfolder 2> error.log
📌 This command tries to list the contents of a nonexistent folder, and the error message (if any) is saved in error.log.

⚠️ **2>> (Appending Error Output)**
➕ Appends error messages to an existing file.

❌ Example: Appending Errors to a File

bash
Copy
$ ls /invalidfolder 2>> error.log
📌 This command appends error messages to `error.log` when trying to list the contents of an invalid folder.

📑 **&> (Redirecting Both Output and Errors)**
🔄 Redirects both standard output and standard error to the same file.

📜 Example: Save Output and Errors Together

bash
Copy
$ ls /home /invalidfolder &> output.log
📌 This command saves both the successful output and error messages from listing the `/home directory` and the nonexistent folder to `output.log`.

🔄 **tee Command (Display and Save Output)**
🔹 The tee command is used to display output on the screen and save it to a file simultaneously.

📜 Example: Save ls Output to a File and Display it

bash
Copy
$ ls | tee filelist.txt
📌 This command lists the files and directories, displays the output on the screen, and saves the same output to `filelist.txt`.

⚡ **Combining Pipes and Redirection**
🔗 You can combine pipes and redirection for advanced operations.

📂 Example: Save Only .txt Files List to a File

bash
Copy
$ ls | grep ".txt" > textfiles.txt
📌 This command filters out .`txt files` from the ls output and saves the filtered list to `textfiles.txt`**.

🔀 Example: Sorting a File and Saving Output

bash
Copy
$ cat names.txt | sort > sorted_names.txt
📌 This command sorts the contents of `names.txt` alphabetically and saves the sorted list to `sorted_names.txt`.

