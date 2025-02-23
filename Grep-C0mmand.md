The grep command is a powerful tool for searching and filtering text in files.

1️⃣ Basic of Grep:


Example:
To search for "error" in `logfile.txt`, you can run:

`grep "error" logfile.txt`

2️⃣ **Grep with Patterns**:

**Match Exact Word** `(-w)`

Matches only whole words. For instance, `grep -w "error" logfile.txt` will not match "errors" or "erroneous".

Case-Insensitive Search `(-i)`

Makes the search case-insensitive, matching "error", "ERROR", "Error", etc.

Example:

`grep -i "error" logfile.txt`

**Count Matches** `(-c)`

Displays the count of lines containing the pattern.

Example:

`grep -c "error" logfile.txt`

Show Line Numbers `(-n)`

Shows the line numbers of the matched lines in the file.

Example:

`grep -n "error" logfile.txt`

3️⃣ **Grep with Wildcards:**

Search in All `.txt` Files

You can use wildcards to search across multiple files. For example:

`grep "error" *.txt`

**Search in Files with Specific Prefix**

This will search in files like `log1.txt`, `log2.txt`, etc.:

`grep "error" log*.txt`

**Recursive Search** `(-r)`

Searches recursively in directories. Example:

`grep -r "error" /var/logs/`

**Exclude Certain Files** `(--exclude)`

You can exclude certain files from the search. For example, to exclude `.log` files:

`grep -r --exclude="*.log" "error".`

4️⃣ **Grep with Regular Expressions** `(-E)`:

Search Multiple Words `(|)`

Use the pipe symbol `(|)` to search for multiple patterns. This will match "error" or "fail":

`grep -E "error|fail" logfile.txt`

Match Start of Line `(^)`

This will match lines starting with "error":

`grep "^error" logfile.txt`

**Match End of Line** `($)`

This will match lines ending with "error":

`grep "error$" logfile.txt`

5️⃣  **Useful Options**

**Option**	                 **Description**    

`-w	`                          `Match whole words only`
`-i`	                         `Ignore case`
`-n`	                         `Show line numbers`
`-r`	                         `Recursive search`
`-c`	                         `Count matching lines`
`-l`	                         `Show filenames with matches`
`--color=auto`	               `Highlight matching words`

🎯 Summary:

`grep` is a versatile tool for pattern searching in files.

Wildcards `(*`, `?`) let you expand your search across multiple files.

Options like `-w`, `-i`, `-n`, and `-r` give you greater control over your search.

Regular expressions `(-E)` open up advanced pattern matching capabilities.




