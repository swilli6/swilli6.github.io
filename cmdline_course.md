---
layout: default
---

## KIK-LG221 Command-Line Tools for Linguists, Fall 2021

![Raptors ahoy](https://www.siliconrepublic.com/wp-content/uploads/2014/12/201503/unix-jurassic-park-718x523.jpeg)

This Bachelor-level course, organized by the department of Languages at the University of Helsinki, ran in Period 1 of the 2021-2022 academic year.

The purpose of the course is to provide students with an introduction to the UNIX Bash shell and to develop skills in using the terminal for processing linguistics resources such as text files and corpora.

### Week 1: Introduction to Command Line Environments
As the course did not require any previous skills in using command-line tools, week 1 involved introducing some very basic Bash skills, such as creating, renaming and removing files and directories, moving from one directory to another, and opening and creating text files using `less` and `nano`.

I had learnt the basics of Bash operations years ago, so the contents of week 1 weren't new, but they were a good reminder of how things work. Somehow Bash also makes more sense to me now than it did in 2008!

### Week 2: Navigating a UNIX System

This week we learnt about processes and programs and what the difference between them is (namely that a process is a single instance of a program running). We also practiced copying files and directories within the local system as well as to and from a server. We also used the `chmod` command to make changes to use permissions on files. 

### Week 3: Basic Corpus Processing

As most of the students taking this course major in Linguistics or other language-related fields, this week is when things started getting exciting as we got to practise processing text files. Some of the commands we learnt this week, such as `tr` and `sort` and saving the output of a command into a file using the `>` symbol became staple operations in this course from now on.

### Week 4: Advanced Corpus Processing

Continuing with processing text files, we learnt how to compare and highlight the differences between two files using the `diff` command. We also dipped our toes into using regular expressions (_regex_), and practised piping commands to form a single long command line, such as the following: 

`cat life_of_bee.txt | tr -s '\n\t\r ' '\n' | tr -dc "A-Za-z0-9'\n" | tr 'A-Z' 'a-z' | sort | uniq -c | sort -nr > life_of_bee.ic.freq`

The command pipeline above does the following:
1. Opens the text file "life_of_bee.txt" for processing
2. Replaces all newline, tab, and carriage return into newline breaks
3. Removes all characters _except_ letters, numbers, apostrophe and newline characters
4. Turns all uppercase letters into lowercase
5. Sorts the results into alphabetical order
6. Removes all duplicate entries
7. Sorts results again into numerical, descending order, and saves the output into file "life_of_bee.ic.freq"

### Week 5: Scripting and Configuration Files

This week was our introduction to writing scripts, which can be quite intimidating if one has no previous experience in coding. However, it soon became apparent that a script is just a set of commands saved into a file! In practical terms, my favourite part of this week was learning to edit the .bashrc file. After adding some colours and formatting, it looked much nicer. If you want to see what I did, add this to your .bashrc file: 

`export PS1="${PURPLE}\d > ${CYAN}\u > ${BROWN}\w >\[$(tput sgr0)\] ${COLOR_NONE}"`

### Week 6: Installing and Running Programs

Now it was time to install Python and learn how to combine running .py programs together with more familiar Unix commands. Creating and building a Makefile took our script writing skills up a notch from last week!

`%.no_md.txt: %.txt`

`python3 src/remove_gutenberg_metadata.py $< $@` 

(indentation missing due to formatting)

The above set of commands is from the Makefile we created this week. It is a recipe to create files of the form bookname.no_md.txt, using files bookname.txt. The Python program _remove_gutenberg_metadata.py_ is applied to each such file, producing the "no_md" text file. The Python program itself removes certain parts of the text (the metadata added to the book text itself by Project Gutenberg).  

### Week 7: Version Control

This week we learnt about the importance of version control and using branches to test experimental features before messing up the working original code. We installed _git_, created our first repositories and practised pushing and pulling (and adding and committing...).

| **Git command**	| **What it does**	| **Why it's important**	|
|-----------------------|-----------------------|-------------------------------|
|`add` | Adds a file to the "stage", waiting to be committed | Easy to forget to do|
|`commit` | Commits changes made | You should always write a note (`-m`) to describe the changes made - these comments last forever!|
|`pull` | Fetches the file from the server to make sure no changes have been made by others whilst you've been editing it | Probably not super important if you're the only one with access to the files|
|`push` | Saves the changes and uploads the updated file into the repository | Do it, or it's all for nought|
|`status` | Lists what has changed since the last push | You'll forget, so use this|


### Week 8: Jekyll and Github Pages

The final week of the course revolved around what you're reading right now - creating and editing Github pages, including cloning templates. The pages are written in Markdown format and converted into HTML using Jekyll, which was a new experience for me (I usually code in HTML directly). Markdown seems to be a very useful way to format text, though.
