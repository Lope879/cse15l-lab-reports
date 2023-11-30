# Lab Report 4 - Vim

## Step 4

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/11e971cf-324f-44a9-9f00-d3fad294daaa)

In the command line, I entered `ssh cs15lfa23ax@ieng6.ucsd.edu` and then `<enter>`. The command `ssh` allowed me to enter a remote computer using my
personal access account. The `<enter>` keypress ran the command. 


## Step 5

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/3d1772c1-13af-4979-831e-5f46282d81bf)

I first copied the ssh url of the forked repository in my github account. Then, inside the remote computer, I entered `git clone git@github.com:ucsd-cse15l-s23/lab7.git`. After the command `git clone` copied the repository into one in the remote computer, I ran the command `ls` to check the repository had successfully copied. 


## Step 6

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/cecb522b-bc63-43f4-8c34-5e69bbbaf8db)

```
cd lab <tab> <enter>

bash te <tab> <enter>
```

I used command `cd` to access the lab7 repository and after used command `bash` to run the bash file "test.sh" which contained the tests that ran and failed. The `<tab>` keypresses helped to fill in the file names found in the repository. 


## Step 7

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/1bae6670-af4b-4044-97ca-7e3cc1a4d598)

```
vim List <tab> .java <enter>

<4> <3> <down arrow> <e> <r> <2> <:> <w> <q> <enter>
```

The `vim` command allowed me to access and edit the ListExamples.java file from the terminal. I then used the down arrows to move my cursor towards the line containing
the error, used `<e>` to move to the end of the word index1, the cursor placed on "1" helped when I clicked `<r>` to initialize a replacement command, and when I clicked `<2>`, the 1 
was replaced by a 2, resulting in "index2". I then saved and quit the file with vim using `<:>` `<w>` `<q>` in normal mode. 


## Step 8

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/50746ae8-d865-42a0-bedf-a7ca8ee173c4)

```
<up arrow> <up arrow> <enter>
```

The up arrows allowed me to search through my history of comamand lines ran previously, which one of them was `bash test.sh`. After running the bash file, the tests ran successfully. 


## Step 9

![image](https://github.com/Lope879/cse15l-lab-reports/assets/100965607/e8565a0f-93d7-4a53-8798-6754175b8563)

```
git add List <tab> <enter> git commit <enter> <i>

change done <esc> <:> <w> <q> <enter> git push <enter>
```

The `git add` command allowed me to add the file changed into a request to confirm its modification. The `git commit` command prompted me to enter a message for the change in vim format, which I had to use `<i>`
to enter insert mode and write the message. After writing the message, I saved and quit using `<:>` `<w>` `<q>`. Finally, I pushed the changed file back to the repository found in Github using 
the command `git push`.
