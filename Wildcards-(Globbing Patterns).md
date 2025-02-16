###Wildcards(Globbing Patterns)

Wildcards (or globbing patterns) are used in computing to represent one or more characters in filenames or strings, typically for pattern matching in searches, shell commands, and scripts. Here's an overview of the most commonly used wildcard patterns:

    Asterisk

Matches zero or more characters. Example:

.txt will match any file that ends with .txt, such as file.txt, document.txt, or even notes.txt.

    Question mark

    Matches exactly one character. Example:

file?.txt will match file1.txt or fileA.txt, but not file123.txt.

    Square brackets []

    Matches any one character within the specified range or set.

You can specify a character range inside the brackets. Example

file[1-5].txt will match file1.txt, file2.txt, etc., but not file6.txt.

You can also specify individual characters: file[ab].txt will match filea.txt and fileb.txt.

    Caret ^ (in square brackets)

Matches any character except the ones specified. Example:

file[^1-5].txt will match files like fileA.txt, but not file1.txt through file5.txt.

    Brace expansion {}

Allows you to specify a list of alternatives. Example:

file{1,2,3}.txt will match file1.txt, file2.txt, and file3.txt.

    Double asterisk (in some contexts, like in bash)

Matches directories or files at any depth (used in recursive patterns). Example:

**/*.txt will match all .txt files in the current directory and all its subdirectories.

Examples of Usage

*.html → Matches any .html file.

data??.csv → Matches files like data01.csv, dataAB.csv but not data123.csv.

image[1-5].jpg → Matches files image1.jpg, image2.jpg, image3.jpg, image4.jpg, image5.jpg.

project{A,B,C}.txt → Matches projectA.txt, projectB.txt, and projectC.txt.
