**Copy (cp), Move (mv), Create (mkdir) and Remove (rm)** 


**Copy File or Directory with cp command:**


**To copy a file from one place to another, use the cp command:**


       Example **cp </path/to/existing/file_name> </path/to/new/location>**


**NOTE:- This will duplicate an existing file into a new location, just like it would if you copied the file and pasted it into another folder.**


**Move File or Directory with mv** :-


**To move a file from one place to another, you canalso use the mv command:**


        **mv </path/to/existing/file_name> </path/to/new/location>**


**Rename Files and Folders with mv** :-


**You can also use the mv command to rename a file or a folder. From the point of view of your operating system, this is the same as cutting and pasting. When you rename something, you move it from one absolute location, which includes the name, to another one.**

        
        **mv file1.txt file2.text**

        
**NOTE:- This will rename file1.txt to file2.txt.**


**Create a Directory with mkdir** :-


**To create a new directory, you can use the mkdir command:**


        **mkdir <directory_name>**

        
**NOTE:- This will create a new folder in the current location you're in. If you provide an absolute path, Bash will create the folder at that location.**


**Create a File with touch** :-


**To create a new file, you can use the touch command:**


        **touch <file_name>**

        
**NOTE :- This will create a new empty file for you with whatever name and extension you specified. Go ahead and use ls to see it in your current directory after you run the touch command.**



**Delete File or Directory with rm** :-



**To delete a file in your current working directory, where your CLI can use its knowledge of relative paths, you can use the rm command:**


        **rm <file_name>**

        
**NOTE :- If you want to delete a file in a different directory than the current one, you can still do so. However, you will need to provide the absolute path to locate the file.**



**If you try to delete a directory in the same way, you will run into an error. This is because Bash wants to avoid accidentally deleting something you don't want to delete.** 


**If you want to delete an empty directory, you can use the rmdir command** :-
        
        
        **rmdir <directory_name>**

        
**NOTE:- This command will delete empty directories. You may notice how it follows a similar naming logic as the mkdir command.**



**Recursively Delete with rm -r** :-


**Often, however, you will want to delete a directory that isn't empty. To do so, you need to employ an option on the rm command combined with the -r (recursive) option:**
        
         **rm -r <directory_name>**

         
**The option -r here stands for recursive, which means that Bash will keep going deeper and deeper inside the directory you provided and delete everything it finds on its way.** 


**The recursive option also exists for some other commands. For example, you can recursively copy a directory, including all its content from one location to another using cp -r <dir_name>**.


**Summary: Linux Copy Directory, Move it and mkdir** :-


•	**This lesson provides instructions to copy, move, delete, and create directories**


•	**These are some of the most common actions when using your CLI**


**Table of Commands Used** :-


**Command	Meaning	Usage** :-


**cp	     -  copy	   - Copy a file**


**mv       -  move	   - Move a file to a different location, or rename it in the same location**


**touch	   -  touch	   - Create a new empty file**


**rm	     -  remove   - Delete a file**


**mkdir	   -  make     -  directory	Create a new empty folder**


**rmdir	   -  remove   - directory	Delete an empty folder. The folder needs to be empty**


**rm       -  r	       - remove -recursively	Delete everything in a nested directory structure, also folders with content**
