# Linux-exercises
from easy to complex linux exercises

----------------Task1--------------------------------

You are required to create an interactive script that collects and displays system information and allows the user to perform various operations. The script must display an interactive menu, wait for a valid option to be entered, and return to the menu after each action, allowing the user to choose a new option or exit the program.

The menu will contain the following options:

Exit – Closes the script.

System Variable Information – Displays the contents of important variables such as the current user, current directory, and the system language (see $USER, $PWD, $LANG).

Display Shells – Displays the first 3 shells of the operating system (see /etc/shells).

Directory and File Management:

Create Directory – The user enters a name, and the script creates that directory.

Navigate to New Directory – After creating the directory, the user can navigate into it.

Create and Copy File – The user enters a filename, the script creates it and copies it into the newly created directory.

Move and Rename Files – Allows the user to enter an existing filename and move it to another directory or rename it.

Delete Directory – Allows the user to enter the name of the directory created in step 4 and delete that directory along with all files inside it.

Display Memory – Displays the total and available memory of the operating system.

Advanced File Search – Allows the user to enter a keyword and search for all occurrences of that keyword in the names of .log files in /var/log/.

Display All Log Files – Displays all log files. A function should be created that receives, as parameters read from the keyboard, a log file name (either current or archived) and a text string, and which will search and display all lines that contain the given text.




-------------------------Task2---------------------------------------------

Create a program in the C language that receives three command-line arguments: a source directory, a destination directory, and a positive natural number.

The program will recursively traverse the directory structure of the source directory. For each entry in the source directory, the following operations will be performed based on the entry type:

For directories, an equivalent directory will be created in the destination directory, with the same permissions as the original directory. Thus, the directory structure in the destination will mirror that of the source.

For regular files, based on their extension:

For files with the .txt extension, the program will count the number of spaces in the file. If the number of spaces is greater than the number given as the third argument, the program will create a symbolic link to that file in the destination directory (preserving the structure), with the same name prefixed with "spaces_". These symbolic links should have the same access rights as the original files.
Example: If a file named file1.txt contains more spaces than the given number, the program will create a symbolic link to that file named spaces_file1.txt.

For files with other extensions, the program will copy the file to the destination directory (and, where necessary, into the appropriate subdirectory). These copied files will have the same read permissions as the original files.
Example: If the original file has permissions -rwx-wxr-x, the new file will have -r-----r--.

For symbolic (soft) links, no operation will be performed.



---------------------------------Task3------------------------------------

A C program is considered, which includes three processes (the parent process and two child processes).

For 5 seconds, the parent process reads information from the file data.txt and sends it through a pipe to the first child process.

The first child process receives the data sent by the parent process through the pipe and forwards all lowercase letters through another pipe to the second child process. In addition, every second, it sends the SIGUSR2 signal to the second child process.

The second child process creates a file named statistica.txt, in which it writes:

The total number of lowercase characters, and

The distribution of lowercase characters (each character and the number of times it appeared), updated after each SIGUSR2 signal.

At the end, the second child process sends the number of distinct lowercase characters through a different pipe to the parent process.

The parent process then displays the result (the number of distinct lowercase characters) in the terminal.
