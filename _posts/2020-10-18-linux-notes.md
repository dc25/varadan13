---
title: "linux notes"
layout: post
theme: 
 
categories: Essays
---

---

> what is a virtual machine?  
>
> -   is a tool to run LINUX OS within WINDOWS ENVIRONMENT  
> -   from VM WARE download VM WARE PLAYER  

> what is LINUX?  
>
> -   Linux is a family of open source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds.  
> -   the word LINUX may refer to 1. the original kernel or 2. the distribution  

> what is LINUX Kernel?
>
> -   KERNEL is some technality related to OS

> what is GNU project?
>
> -   to create free softwares  
> -   free software are different from open source software
> -   Roughly free software under GNU means that the users have the freedom to run, copy, distribute, study, change, and improve the sotware
> -   FOSS #I have come across this acronym although much thought was not put into it but now it is clear that this FOSS brings free software and open source groups together becuase the acronym expands to free and open source software.

> what is GNU?
>
> -   GNU is a self referential acronym and it is infinite in that sense. GNU = GNU is not UNIX.  
> -   GNU may be refered to the collection of free softwares 
> -   it was started by # Richard Stallman 

### open source has its differences with GNU free software.

the command prompt will look like  

aneesh@ubuntu:~$  -> what is the syntax?  

aneesh -> user name; @ubuntu -> is the host name; ~$ -> tells that the working directory is home.

the command to view the current working directory.  

    	aneesh@ubuntu:~$ pwd  
		# /aneesh/desktop
        

"cat" is the command to read a file.

    	aneesh@ubuntu:~$ cat desktop/file_to_be_read
        

"ls" is the command to list all the files in the current working directory
{% highlight ruby %}


    	aneesh@ubuntu :~$ ls  
		## returns all the file name  
		# then to address any file I just have to write the name for example desktop/new
{% endhighlight %}       

"ls -l" "ls -a" to view file comprehensively and to view files that are hidden in the working directory respectively

    	aneesh@ubuntu :~$ ls -l
        
        ##
        
        aneesh@ubuntu :~$ ls -a
        
        ##

### what are dot files?

-   hidden files in linux is called dot files

"clear" is the command to clear the window of prompt. "ls -la" is the combination of "ls -l" and "ls -a" 

"cd" is the command to change directoy 

    	aneesh@ubuntu :$ cd desktop
        
        aneesh@ubuntu :desktop$ ls
        
        ##
        
        aneesh@ubuntu :desktop$ cd ..
        aneesh@ubuntu :$ ls
        
        ##
        
        aneesh@ubuntu :xyz$ cd #in case Iam lost. typing this put me back into home directory
        aneesh@ubuntu :$ ls
        
        ##
        

how to create files via terminal. use "mkdir" . this "mkdir" makes file in the current directory.  
to remove a folder/directory in the current directory use "rmdir". 

    	aneesh@ubuntu :$ cd desktop
        aneesh@ubuntu :desktop$ mkdir newfolder
        aneesh@ubuntu :desktop$ mkdir new2
        aneesh@ubuntu :desktop$ rmdir new2
        aneesh@ubuntu :desktop$ ls
        ## new 2 will have been removed in the desktop which is the current working directory
        

use "touch" keyword to add txt files in the cd

    	aneesh@ubuntu :desktop$ touch emdscvir
        
        aneesh@ubuntu :desktop$ ls
        ## a txt file named emdscvir will have been created in the cd.
        
        aneesh@ubuntu :desktop$ rm emdscvir # not rmdir for txt files
        ## this removes emdscvir from current cd
        

use "cp" make a copy of a file in the cd

    	aneesh@ubuntu :desktop$ cp newfolder newfolder_2
        

use "mv" to mv a file from a directory into another.  

    	aneesh@ubuntu :desktop$ mv newfolder_2 other/newfolder_3
        ## it deletes the file newfolder_2 in desktop and creates a file called newfolder_3 in other which is in desktop.
        aneesh@ubuntu :desktop$ mv newfolder_2 tuna
        ## it deletes newfolder_2 in the CD and creates tuna in the CD.

my doubt is how to move a file into a directory that is in opposite direction?

the command to find differences in two documents is diff.  
lets say in desktop directory there are 2 files x and y both are similar text file with minor difference

        aneesh@ubuntu :desktop$ diff x y
    	## it is going to print out the differences in x and y file
        
        aneesh@ubuntu :desktop$ name = aneesh
        aneesh@ubuntu :desktop$ echo hey 
        
        ## hey
        
        aneesh@ubuntu : desktop$ echo hey $name
        
        ## hey aneesh
        

2 things to notice in the above code.  
a> echo is command that displays wat ever is written after it.  
b> $name is a way to tell LINUX that name is a variable so that it reads the value of the variable 'name'  

    	aneesh@ubuntu :desktop$ echo hey name
        
        ## hey name # but i want the display hey aneesh since name == aneesh.

how to find details of a command in LINUX like ? in R. use info nameOfTheCommand

    	aneesh@ubuntu :desktop$ info echo
        
        ## prints out all the gory details of that function
        >press ctrl + z to go back to the home page of the terminal
        aneesh@ubuntu :desktop$ clear
        

### stopped at tutorial 7.
