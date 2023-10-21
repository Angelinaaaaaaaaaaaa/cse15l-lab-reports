# Lab Report 1

Command 1
## `cd`

![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/e7942ecc-8cbd-4ce0-91e4-fce4bc77cd26)
  After I tried the `cd` command with no arguments, I got nothing in the output. When this command was run, the working directory was `/home`. There was no output displayed in the terminal, but the working directory was changed to the root directory(which would be shown more clearly in different cases). This means that using `cd` with no arguments changes the working directory to the highest-level directory.

  After I tried the `cd` command with a path to a directory as an argument, there is nothing in the output, but the working directory is now changed into '~\lecture1'. This is due to the fact that I changed the directory using the 'cd' command.

  After I tried the `cd` command with a path to a file as an argument, I got an error message saying that it was not a directory. It is an error because cd is used for changing directories(change to the location of directories), which is not applicable to files. The working directory now is '~/lecture1'.


Command 2: 
## `ls`
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/d2301b69-5353-4897-82d3-12a4ff6c183d)

  After I tried the `ls` command with no arguments, I got lecture1 in the output because it shows what is at the location `/home` without errors. The output in the terminal was all the folders and files under the current directory. This means using 'ls' with no arguments lists out all the content under the current working directory by default.

  After I tried the `ls` command with a path to a directory as an argument, I got things in lecture1 in the output without errors because it shows what is at the location /home/lecture1. This means using 'ls' with a directory as the argument lists out the content under that directory.

  After I tried the `ls` command with a path to a file as an argument, I got lecture1/Hello.java itself without errors because there is nothing more in this absolute location of a file.


Command 3:
## `cat`
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/2fff89ae-fb19-444f-982f-429f904c5901)

  After I tried the `cat` command with no arguments, I got nothing(no errors or outputs) in the output because the `cat` command could only read each File parameter in sequence and write it to standard output, and the current working directory is `/home`. The terminal started an interactive session, displaying whatever I entered right after on the next line.
  
  After I tried the `cat` command with a path to a directory as an argument, I got an error message in the output because the location `/home/lecture1` is a directory instead of a file, which suggests that the `cat` command can only be used with a file as the argument.
  
  After I tried the `cat` command with a path to a file as an argument, I got a Hello World message in Russian because the ls command successfully writes the text in the file. The working directory is `/home`, and it produces no errors, which means that the 'cat' command concates contents in .txt file that is at the path provided.
