Command 1: cd
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/e7942ecc-8cbd-4ce0-91e4-fce4bc77cd26)
The working directory is /home.
After I tried cd command with no arguments, I got nothing in the output because it basically does nothing.
After I tried cd command with a path to a directory as an argument, there is nothing in the output, but the working directory is now changed. This is due to I changed the directory using the cd command.
After I tried cd command with a path to a file as an argument, I got an error message saying that it is not a directory. It is an error because cd is used for changing directories(change to the location of directories), which is not applicable to files.


Command 2: ls
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/d2301b69-5353-4897-82d3-12a4ff6c183d)
The working directory is /home.
After I tried ls command with no arguments, I got lecture1 in the output because it shows what is at the location /home.
After I tried ls command with a path to a directory as an argument, I got things in lecture1 in the output because it shows what is at the location /home/lecture1.
After I tried ls command with a path to a file as an argument, I got lecture1/Hello.java itself because there is nothing more in this absolute location of a file.


Command 3: cat
![image](https://github.com/Angelinaaaaaaaaaaaa/cse15l-lab-reports/assets/115201846/2fff89ae-fb19-444f-982f-429f904c5901)
The working directory is /home.
After I tried cat command with no arguments, I got nothing in the output because cat command could only read each File parameter in sequence and write it to standard output, and the current working directory is /home.
After I tried cat command with a path to a directory as an argument, I got an error message in the output because the location /home/lecture1 is a directory instead of a file.
After I tried cat command with a path to a file as an argument, I got a Hello World message in Russian because the ls command successfully writes the text in the file.
