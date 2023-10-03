**LAB REPORT 1**

Command cd:
***
1) No Argument:
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd
[user@sahara ~]$ pwd
/home
```
The working directory was "/home" before it was run and it remained the same after running.

After running "cd" by itself, nothing was printed and the working directory remained the same because the command cd did not 
have any argument to use as a new path.

Not an error.


2) Path to a Directory:
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The working directory was "/home" before running, then changed to "/home/lecture1".

The working directory changed since command cd used "lecture1" as its argument to change the working directory to the new given path.

Not an error.


3) Path to a File:
```
[user@sahara ~/lecture1/messages]$ cd lecture1/messages/en-us.txt
bash: cd: lecture1/messages/en-us.txt: No such file or directory
```
The working directory was "/home/lecture1/messages" and remained as is after running the code.

I received the output that no file or directory was found since cd requires a directory to be used as an argument and thus change the working directory, 
but instead a file was given as the argument and thus caused an error since cd couldn't work properly without a proper argument.

This was an error.



Command ls:
***
1) No Argument:
```
[user@sahara ~]$ ls
lecture1
```
The working directory was "/home" before and after the code ran.

Command ls listed the files found inside the current working directory which is /home which contained only /lecture1 and thus printed it.

Not an error.


2) Path to a Directory:
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
The working directory was "/home" before and after the code ran.

The command ls printed the files found inside the directory "/lecture1" which where correctly listed.

Not an error.

4) Path to a File:
```
[user@sahara ~/lecture1/messages]$ ls en-us.txt
en-us.txt
```
The working directory was "/home/lecture1/messages" when the code ran.

The command ls accepted the file "en-us.txt" as an argument and printed its file name instead of its contents because the file could 
not contain other files or folders.

This 


Command cat:
***
1) No Argument:
```
[user@sahara ~]$ cat

```
The working directory was "/home" when the code ran.

The command cat tried to print files but without an argument it did not run properly and instead prompted the programmer to write, which meant that the terminal 
could not end as expected and thus turned into an error.

This was an error.


2) Path to a Directory:
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
The working directory was "/home" when the code ran.

The command cat tried to print lecture1 but since it is not a file, it could not print its contents and instead stated that it was a directory.

Not an error since the code ran as expected and no file was found to write its contents.


4) Path to a File:
```
[user@sahara ~/lecture1/messages]$ cat en-us.txt
Hello World!
```
The working directory was "/lecture1/messages" when the code ran.

The command cat printed the text content inside the file named "en-us.txt" correctly. 

Not an error.
