### Linux Introduction
Linux is a Unix like operating system. It is open source and free. We might sometimes use the word "Unix" instead of Linux.

A user can interact with Linux either using a 'graphical interface' or using the 'command line interface'.

Learning to use the command line interface has a bigger learning curve than the graphical interface but the former can be used to automate very easily. Also, most of the server side work is generally done using the command line interface.

### Linux Operating System
The operating system is made of three parts:

#### The Programs

A user executes programs. Chrome is a program that gets executed by the kernel, for example. When a program is launched, it creates processes. Program or process will be used interchangeably.

#### The Kernel

The Kernel handles the main work of an operating system:

Allocates time & memory to programs
Handles File System
Responds to various Calls

#### The Shell

A user interacts with the Kernel via the Shell. The console as opened in the previous slide is the shell. A user writes instructions in the shell to execute commands. Shell is also a program that keeps asking you to type the name of other programs to run.


### Linux Files & Processes
Everything in Unix is either a file or a process.

#### Process

When you run a program, a process is created. Every process is identified by a number called process ID. To check the processes you are running, execute "ps" command on the shell. You can think of the process ID to be a sequence number given by the operating system. It may be different at different execution of the same program.

#### File

A file is a sequence of data. A file could be created by users using word processors or text editors or by the program to keep the information. A program is kept in the form of a file and when it is run by the kernel, it loads as a process.

A file is generally written on the disk so that it exists even after the computer restarts. It is saved in a disk - either hard disk drive (HDD - cheaper and slower) or solid state drive (SSD - faster but costlier).

A file is identified by a name called file path. In Unix, everything is represented as file:

* Devices such as Mouse, Keyboard
* Programs are saved as file
* Disk and Monitor

### The Directory Structure
A file is kept inside a directory. A directory can have a file or another directory inside it. It is like an inverted tree.

The top-level directory is "/" called root. "/" directory does not have a parent. /A/B means B is inside A which is inside the top-level directory "root" denoted by /.

<img src=https://www.devopsdexter.com/wp-content/uploads/2020/05/linux-filesystem.png style=" background-color:white;">

List Files and Directory
To see the list of files use the command: `ls`

Relative & Absolute Paths - Change the Directory
There are two ways to represent a file/directory path:

Absolute: This way of representing a file/directory is independent of the current directory of the user. Such paths start with "/". <b>Example:</b> The absolute path is the path of the directory from the root directory, like the path of 'john' directory, is actually '/home/john' as you can see in the tree structure

Relative: Relative to the current working directory. <b>Example:</b> Consider that you're currently in directory `projects`, the relative path from directory `projects` to directory `john` would be `../../../home/john` it is like tracing the path back to / then to john.

You can change the directory using the cd command. Every user is given a separate home directory.

Home Directory & Current Directory
Inside the console, you are always in a directory. On login, by default, you land in your home directory.

To see the present working directory use: `pwd`

To change the directory to your home directory use only `cd` command without any arguments.

### Create Directory
You can create the directory using `mkdir` command in the following way:
```
mkdir <directoryname>
```

### Create Directory - nested
If you have to create a directory within the directory, it is easier to use `mkdir -p`. To learn more about mkdir using manual:
```
man mkdir
```

### Delete a file
To delete a file you can use rm command. To delete the directory use `rm -r`

### Create File
A file is a sequence of bytes and represents data. It is found in a directory. A file could contain any kind of data: an executable program, data representing movies, music, pictures or plain text.

You can create an empty file using `touch` command. Please note that the extension of the file doesn't matter much in Unix.

### Create Text File Using Nano

You can use a text editor to edit or create a text file. There are many editors in Linux such as nano, pico, vi, emacs. Let's try to use nano for creating a file

1. Launch nano to edit:
    ```
    nano myfirstfile.txt
    ```
2. Type the following text into it:
    ```    
    He walked into his exile
    ```
3. Press `Ctrl+x`, you will get a prompt at the bottom of the screen asking you to "Save modified buffer (Answering No will DESTROY CHANGES)". Press `y` as we want to save the changes, and then Enter to Save Changes and exit the nano editor.

4. Alternatively you can create the file with this command
    ```
    echo "He walked into his exile" > ~/myfirstfile.txt
    ```

### Copy File
To copy files and directories we use the `cp` command

### Copy a file into another directory
1. Create a directory with a name `myproject` using the command:
    ```
    mkdir myproject
    ```
2. Copy the file `myfirstfile.txt` created in the previous exercise to `myproject` directory
    ```
    cp myfirstfile.txt myproject
    ```
### Copy a directory into another directoryname

1. Create a directory "src"
    ```
    mkdir src
    ```
2. Create a file in "src"
    ```
    touch src/myfile.txt
    ```
3. Create a directory "proj"
    ```
    mkdir proj
    ```
4. Copy the src into "proj"
    ```
    cp -r src proj
    ```
### Move Files & Directories
`mv` command is used to move or rename files and directories.

1. Create a file myfirstfile.txt.

    ```
    nano myfirstfile.txt
    ```
2. Add the text `a clever fox` into the editor and press `ctrl+x`, followed by `y`, and then enter to save the file and come out of the nano editor.

3. Rename `myfirstfile.txt` to `firstfile.txt`.
    ```
    mv myfirstfile.txt firstfile.txt
    ```

### Move a file to folder
1. Create a directory mywork in your home folder
    ```
    mkdir mywork
    ```
2. Move the file firstfile.txt created earlier to mywork
    ```
    mv firstfile.txt mywork
    ```

### Delete Files & Directories
To delete a file or a folder, use `rm` command

```
Delete the file mywork/firstfile.txt created in the previous step.
```

### Seeing Inside File - cat, tail, head
To see what is inside a text file, you can use either `cat`, `tail` or `head` command.

Using `cat` you can see the whole content of the file:
```
cat myfirstfile_copy.txt
```

Do not use this command to look inside a huge file. For the huge file, you can use the `more` command which would display the content of a file in a paginated way:
```
more myfirstfile_copy.txt
```
`tail` shows you the last few lines of a file

```
tail myfirstfile_copy.txt
```

By default `tail` shows you only last 10 lines, you can change it using the command line option. For example, to see the last 20 lines, you can use
```
tail -20 myfirstfile_copy.txt
```

Say you want to see the web server's (Apache, Nginx) access log of your website. Logs will keep on getting appended to access.log file when visitors visit your website. Now you can run below command and keep it running. It will keep on printing newly added lines in the access.log.
```
tail -f access.log
```

If you are interested in the first few lines, you can use the `head` command. By default `head` shows you only first 10 lines, you can change it using the command line option. For example, to see the first 20 lines, you can use

```
head -20 myfirstfile_copy.txt
```
### Use find command
Sometimes you might want to search for a particular file based on various attributes of a file such as size or name etc. The `find` command comes very handily for such use cases.

For example, to find all the text files in the current directory, you can use this command
```
find . -name '*.txt'
```

### Use grep command
If you want to locate a word in files, you can use the `grep` command. Grep lists all the lines from files in which a particular word exists. Examples of grep
```
grep myword file1 file2
```
If you want to search in files recursively - inside every subdirectory of a directory, use the following command
```
grep -r myword directory
```
If you want to search case insensitive, use -i switch
```
grep -i myword file1 file2
```
Practical Use Cases
`grep` is a very powerful tool. It can somewhat behave like where clause in SQL queries.

Few Examples are:

1. On a web server, you could filter only the errors from a log file
2. Say you have a directory containing the temperature of various cities and you are looking for temperatures of the city having the name as nyc, you could easily do: 
`grep nyc tempdirectory/*`

### Use wc command
To find the number of lines, words, and characters, use `wc` command.

If you are only looking for number of lines you could use:
```
wc -l
```

### Permissions - Overview
Permissions in Unix are an integral part of the operating system.

You can see the details of a file using `ls -la` command:
```
ls -la myfile
```
And you can see the details of all files in the current directory by using:
```
ls -la
```
Every file has an owner (also referred to as the user), a group and permissions. A user can be part of many groups. A group can have many users.

<img src="https://s3.amazonaws.com/cloudxlab/static/images/aha/ls-al.png">

The permission attributes of a file signify who can do what.

<img src="https://s3.amazonaws.com/cloudxlab/static/images/aha/file-permissions-rwx-1024x340.jpg">


### Permissions - Using chmod To Change
You can change the permissions of a file using `chmod` command: `chmod permission_cmd myfile`

You can allow or disallow the user (u), group (g) or other(o) the following actions: read (r),  write (w) and execute (x).

So, if you want to allow the user (the person who owns it) to execute the file:
```
chmod u+x myfile
```
And to disallow the user (the person who owns it) to execute the file:
```
chmod u-x myfile
```
Say you want to give the rw (read & write) permissions to owner and group of a file, you will have to use the following command:
```
chmod u+r,u+w,g+r,g+w myfile

    or

chmod u+rw,g+rw myfile
```
To give members of a group ability to modify a file, use:
```
chmod g+w myfile
```

### Permissions: Assignment - Owner can change, others can only read
1. Create a new file called myemptyfile in your home directory. You can use:
```
cd ~
touch myemptyfile
```
2. Check its permissions using:
```
ls -l myemptyfile
```

#### INSTRUCTIONS
* Go to your home directory using `cd ~`
* If the file `myemptyfile` doesn't exist, create it using `touch myemptyfile`
* Using `chmod`, give it permissions such that only the Owner of a file should be able to modify. Everyone else (Group and Others) should be able to only read.
* `ls -l myemptyfile` should print something like this:
```
-rw-r--r-- 1 user123 user123 0 Oct 24 07:40 myemptyfile
```
Answer:
```
cd ~
touch myemptyfile
ls -l myemptyfile
chmod o-w,g-w myemptyfile
ls -l myemptyfile
```
### Permission: Assignment - Everyone can execute
Ignore the below instructions if you have already created myemptyfile file in the previous question

1. Create a new file called myemptyfile in your home directory. You can use:
```
touch myemptyfile
```
2. Check its permissions using:
```
ls -l myemptyfile
```

Using chmod, give it permissions such that the owner of the file should be able to modify. Everyone should be able to execute but no one other than the owner can modify the file. Give permission to the file such that

* The owner of the file should be able to modify
* Everyone (Owner, Group, Others) should be able to execute
* None other than the owner can modify (or write to) the file

Answer:
```
cd ~
ls -l myemptyfile
chmod +x myemptyfile
ls -l myemptyfile
```
