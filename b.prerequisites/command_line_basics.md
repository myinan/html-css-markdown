# Command Line Basics

## [The Unix Shell (bash) Basic Course by the Software Carpentry Foundation](https://swcarpentry.github.io/shell-novice/)

The Unix shell is both a command-line interface (CLI) and a scripting language. <br>

The most popular Unix shell is Bash (the Bourne Again SHell — so-called because it’s derived from a shell written by Stephen Bourne). Bash is the default shell on most modern implementations of Unix. <br>

These three commands are the basic commands for navigating the filesystem on your computer: pwd, ls, and cd. <br>


### Navigating Files and Directories Keypoints
+ The file system is responsible for managing information on the disk.
+ Information is stored in files, which are stored in directories (folders).
+ Directories can also store other directories, which then form a directory tree.
+ pwd prints the user’s current working directory.
+ ls _path_ prints a listing of a specific file or directory; ls on its own lists the current working directory.
+ cd _path_ changes the current working directory.
+ Most commands take options that begin with a single -.
+ Directory names in a path are separated with / on Unix, but \ on Windows.
+ / on its own is the root directory of the whole file system.
+ An absolute path specifies a location from the root of the file system.
+ A relative path specifies a location starting from the current location.
+ . on its own means ‘the current directory’; .. means ‘the directory above the current one (e.g. the parent directory)'.


### Working With Files and Directories Keypoints
+ cp _old_ _new_ copies a file.
+ mkdir _path_ creates a new directory.
+ mv _old_ _new_ moves (renames) a file or directory.
+ rm _path_ removes (deletes) a file.
+ "*" matches zero or more characters in a filename, so *.txt matches all files ending in .txt.
+ "?" matches any single character in a filename, so ?.txt matches a.txt but not any.txt.
+ Use of the Control key may be described in many ways, including Ctrl-X, Control-X, and ^X.
+ The shell does not have a trash bin: once something is deleted, it’s really gone.
+ Most files’ names are something.extension. The extension isn’t required, and doesn’t guarantee anything, but is normally used to indicate the type of data in the file.
+ Depending on the type of work you do, you may need a more powerful text editor than Nano.


### Pipes and Filters Keypoints
+ wc counts lines, words, and characters in its inputs.
+ cat displays the contents of its inputs.
+ sort sorts its inputs.
+ head displays the first 10 lines of its input.
+ tail displays the last 10 lines of its input.
+ command > [file] redirects a command’s output to a file (overwriting any existing content).
+ command >> [file] appends a command’s output to a file.
+ [first] | [second] is a pipeline: the output of the first command is used as the input to the second.
+ The best way to use the shell is to use pipes to combine simple single-purpose programs (filters). (a filter is a program like wc or sort that transforms a stream of input into a stream of output. Almost all of the standard Unix tools can work this way. Unless told to do otherwise, they read from standard input, do something with what they’ve read, and write to standard output.) (example: $ cat animals.csv | head -n 5 | tail -n 3 | sort -r > final.txt)


### Loops Keypoints
+ A for loop repeats commands once for every thing in a list.
+ Every for loop needs a variable to refer to the thing it is currently operating on.
+ Use {dollar.sign}name to expand a variable (i.e., get its value). "dollar.sign{name}" can also be used.
+ Do not use spaces, quotes, or wildcard characters such as ‘*’ or ‘?’ in filenames, as it complicates variable expansion.
+ Give files consistent names that are easy to match with wildcard patterns to make it easy to select them for looping.
+ Use the up-arrow key to scroll up through previous commands to edit and repeat them.
+ Use Ctrl+R to search through the previously entered commands.
+ Use history to display recent commands, and ![number] to repeat a command by number.
+ In bash, loops can also be nested.


### Shell Scripts Keypoints
+ Save commands in files (usually called shell scripts) for re-use.
+ bash [filename] runs the commands saved in a file.
+ $@ refers to all of a shell script’s command-line arguments.
+ $1, $2, etc., refer to the first command-line argument, the second command-line argument, etc.
+ Place variables in quotes if the values might have spaces in them.
+ Letting users decide what files to process is more flexible and more consistent with built-in Unix commands.


### Finding Things Keypoints
+ find finds files with specific properties that match patterns.
+ grep selects lines in files that match patterns.
+ --help is an option supported by many bash commands, and programs that can be run from within Bash, to display more information on how to use these commands or programs.
+ man [command] displays the manual page for a given command.
+ $([command]) inserts a command’s output in place.


## The Unix Shell (bash) Basic Course by the Software Carpentry Foundation == COMPLETED

---

**First**, you might have already noticed that copying and pasting inside the command line doesn’t work the way that you’d expect. When you’re inside the command line, you’ll need to use Ctrl+Shift+C (Mac: Cmd+C) to copy and Ctrl+Shift+V (Mac: Cmd+V) to paste. For example, to copy and paste commands from your browser into the command line, you’ll highlight the command text and use Ctrl+C as usual and then paste it in your terminal using Ctrl+Shift+V. <br>

**Second**, you need to learn about tab completion. Seriously, this tip will save you so much time and frustration. <br>

**Third**, there’s a really handy shortcut for opening everything within a project directory: **.** Once you’ve installed a text editor, you can use this shortcut(.) to open up an entire project and all its files in one go. <br>

---

## Knowledge Check
**Q1.** What is the command line?

**A1.** Command Line is the interface used for giving instructions to the computer's hardware. With CLI, many commands that we can give to the computer through the GUI(Graphical User Interface) can also be used but on top of that CLI provides us tools that we can automate more complex tasks that we can't really automate through the use of GUI. We can create pipelines, loops, scripts and programs with the use of Command Line.

**Q2.** How do you open the command line on your computer?

**A2.** Since i'm using Xubuntu (A distro of Ubuntu), i use "CTRL+ALT+T" to open the command line. 

**Q3.** How can you navigate to a particular directory?

**A3.** The command "cd" can be used to navigate through directories.

**Q4.** Where will cd on its own navigate you to?

**A4.** If "cd" command is used on it's own, it will navigate to the home directory.

**Q5.** Where will cd .. navigate you to?

**A5.**"cd .." navigates to the parent directory of the current working directory.

**Q6.** How do you display the name of the directory you are currently in?

**A6.** "pwd" (print working directory) command is used to display the name of the current working directory in bash.

**Q7.** How do you display the contents of the directory you are currently in?

**A7.** "ls" command displays the contents of the current working directory.

**Q8.** How do you create a new directory?

**A8.** "mkdir" command is used to create a new directory.

**Q9.** How do you create a new file?

**A9.** We can use "touch" command to create a file, create and open a file with nano text editor with the command "nano filename.extension", we can also use command "code" to create a file.

**Q10.** How do you destroy a directory or file?

**A10.** The command "rm filename" is used to remove a file from the system. "rm -r directory-name" is used to remove a directory from the filesystem. The "-r" option is used to remove directories.

**Q11.** How do you rename a directory or file?

**A11.** "mv old-name/dir new-name/dir" is used to rename(move) a directory or file in bash.