# [[Linux Basics for Hackers Getting Started with Networking, Scripting, and Security in Kali]]

### Snort and File Viewing Commands

This chapter discusses the use of Snort for network intrusion detection. However, I do not have Snort installed on my system, so I won’t be following along with those exercises.

### Viewing the First Few Lines of a File

- **head `<filename>`**: Displays the first few lines of a file.
  - **Syntax to specify line count**: `head -<number_of_lines> <filename>`

### Viewing the End of a File

- **tail `<filename>`**: Displays the last few lines of a file.
  - The syntax for `tail` is similar to `head`.

### Filtering with `grep`

- **Syntax**: `cat <filename> | grep "<keyword>"`
- Example: Use `grep` to filter for specific keywords in a file.

### Using `sed` to Find and Replace Text

You can use `sed` to find and replace text within a file. For example, if you have the word "mysql" in lowercase and you want to replace it with "MySQL," you can use the following syntax:

- **Syntax**: `sed s/<word_to_change>/<replacement_word>/g <original_filename> > <new_filename>`

**Example with `sed`**:
```bash
# Creating the file using nano
$ nano cat.txt

# Display the contents of the file
$ cat cat.txt
This is a test I am doing this to change mysql to MySQL using sed command 

# Using sed to replace "mysql" with "MySQL" and save to a new file
$ sed s/mysql/MySQL/g cat.txt > cat2.txt

# Display the contents of the updated file
$ cat cat2.txt
This is a test I am doing this to change MySQL to MySQL using sed command 
```

### Viewing Files with `more` and `less`

- **more `<filename>`**: Displays the file one page at a time.
  - I wondered if this would work with a PDF. I tested it by downloading a threat hunting PDF just for fun.
- **less `<filename>`**: Another command for viewing files. I was able to use `less` to display the PDF file.
  - **To exit**: Press the letter `q`.

### Numbering Lines in a File with `nl`

- **nl `<filename>`**: Numbers all the lines in the text file.
- I found this command interesting and realized I hadn’t encountered it in the chapter earlier. It was great to discover this during the exercise portion.

---
