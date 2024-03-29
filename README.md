## Over-The-Wire
The wargames offered by the OverTheWire community can help teach and practice security concepts in the form of fun-filled games.  Bandit is recommended for absolute beginners.  If you've never opened linux before but you're interested in security this can help you get there.  To level up to one and capture the metaphorical flag, usually a string of random characters, you must SSH or log into the game server.  SSH stands for Secure Socket Shell or Secure Shell, and to learn how to syntactically arrange all our information to log in can be found in the manual by typing `man ssh`.  It will then show you a list of all the correct syntax for common options
![image](https://user-images.githubusercontent.com/113439757/191985509-a83eedc1-3f19-4733-8008-3d689eed8991.png)

Judging from this, and the information given on the website, we need to invoke ssh input the user@serverlocation and the port number since they want a connection on the nonstandard port 2220.
It should look like this `ssh bandit0@bandit.labs.overthewire.org -p 2220`.  After that, you'll have to enter the password for the server (bandit0) supplied on the website. Congratulations you have succcessfully completed the first task!

# Level 0 > 1
Now that you are logged in, the instructions state "The password for the next level is stored in a file called readme located in the home directory."  We have some hint commands available to us on the level goals page too which are pwd, ls, cat, cd, du, file, and find.  After logging in, you can see what directory you are in at any given time with the command `pwd`.  Pwd stands for print working directory.  Typing this command we can see we are already in the home directory, so the readme file should be here.  We can also look at the contents of the directory using `ls` which stands for list directory contents and it will show us information about the files. We can type the command to confirm this.  To print the contents of the file we use the `cat` command followed by the filename as written when we typed ls and we have our answer.

![image](https://user-images.githubusercontent.com/113439757/192812957-bc034ea8-086b-4817-addd-fa91b2f5b940.png)

Are there other ways to arrive at our answer? Absolutely! The one above is probably the most beginner friendly, but if you know already how to tie commands together with the pipe symbol `|` then you could also do something like `find * | cat *` to arrive at the same answer for this specific situation.  The same would apply to `file -f readme`,  `head readme` or `awk '{print $1}' readme`.  Learning multiple ways to perform a task is critical to enhancing literacy and articulating specificity! 
![image](https://user-images.githubusercontent.com/113439757/192873847-73cb4bf9-428a-46ee-b8ed-d348cd545a37.png)

# Level 1 > 2
Use the same method to log into level 1 as you did level 0. The directions are "The password for the next level is stored in a file called - located in the home directory" and the helpful commands are the same as before.  Now we have helpful reading material as well; specifically http://tldp.org/LDP/abs/html/special-chars.html which is a guide to special characters in bash scripts.  Knowing that our instructions are similar in format to the previous quesiton, so too should then our investigation be conducted.  Gathering information is the first step, so we need to find out what folder we are dumped in after login. we use `pwd` and it tells us that we are in the home directory where we need to be. From there we can use `ls` to see our file - is present.  If we just try to cat to this file like we did in the previous exercise we get a blank terminal that simply repeats whatever we type.  Thats because a `cat -` command echoes stdin, in this case keyboarded user input, to stdout. `-` is not itself a Bash operator, but rather an option recognized by certain UNIX utilities that write to stdout, such as `tar`, `cat`, etc. Where a filename is expected, `-` redirects output to stdout (sometimes seen with `tar cf`), or accepts input from stdin, rather than from a file. This is a method of using a file-oriented utility as a filter in a pipe. The `-` can be used to pipe stdout to other commands. This permits such stunts as prepending lines to a file. For example, using `diff` to compare a file with a **section** of another.  We have to escape the recognition as an option and show it is a file.  we do this with `./` which calls something in the current directory.

![image](https://user-images.githubusercontent.com/113439757/193274366-18c43089-bb3a-4081-94dd-cae71836de53.png)

# Level 2 > 3
The level instructions state "The password for the next level is stored in a file called spaces in this filename located in the home directory" so we login and see we are in the home directory to start.  If we try to `cat spaces in this filename` the terminal tries to cat each word as a file name instead of as one.  Whereas in the previous level we wanted to seperate a filename from something, this time we want to include something(whitespace) with the filename.  To do that we use single quotes, both on linux and windows, to denote that it is a string. 
![image](https://user-images.githubusercontent.com/113439757/193277126-c220ae18-cc27-49f6-b800-ba65cbba3dac.png)

# Level 3 > 4
The level instructions state "The password for the next level is stored in a hidden file in the inhere directory".  We follow our method until we get inside the inhere directory.  We can type `ls` but nothing comes up because the file is hidden.  There are several ways to find this hidden file, the most straightforward being to look at the `man ls` page and see that the option `-a` does not ignore entries starting with `.`. 
![image](https://user-images.githubusercontent.com/113439757/193285278-bba90cb4-5c08-4997-9e82-d7554c964b29.png)

Personally I prefer `ls -la` because it also shows file permissions and ownership and just looks cleaner.  As a side note, you can also write it `ls -al` which threw me for such a loop the first time I saw it -I actually thought it was a different command than `ls -la`. I challenge you to find at least 4 ways to discover this file using the helpful commands section of the instructions page!

# Level 4 > 5
The level instructions state "The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the \u201creset\u201d command."  After going into the folder we see a number of files that if we `cat` to the terminal give us gibberish.  we could do this for each one and find the only one we can read.  My dad used to always say that it's not stupid if it works.  But we are here to sharpen our skills and learn something new that the previous lesson did not offer! The simpliest way to do that would be to use the `file` command to output each file's type as shown in the `man` page. To do that we type `file ./*`.  The * is a wildcard that runs the command on every file in the directory.  The only one we can read is ascii.

![image](https://user-images.githubusercontent.com/113439757/193299869-516e6665-5eec-4851-897a-051183c6f8ad.png)

I looked at a few other walkthroughs trying to find alternate solutions beyond this one but the find related one is the only one listed pretty much everywhere except one.  There was a find based loop but I was looking specifically for ways to avoid the find command and still efficiently print the results without having to check each file individually.  If you use the strings command as so `strings ./*` it will give you the flag without having to even use the cat command.  I recognize that it is beyond the scope of the helpful commands in the exercise, but if there are others you know of please reach out to me, I'd love to see what you come up with.

![image](https://user-images.githubusercontent.com/113439757/193302217-24b0071b-b750-48b7-9760-6573ca851476.png)


# Level 5 > 6
The level goal states: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:human-readable, 1033 bytes in size, and not executable.  We could use the `file` command as in the last exercise to locate the human readable file but lets go another route. We haven't really explored the `find` command yet and this is a reasonable way to search data. A look through our manual yields the proper arguments to add `-type f -size 1033c` based on the level goals information.
![image](https://user-images.githubusercontent.com/113439757/195918536-9e09ed92-e9a3-48a4-bb3d-2557b4adfa1a.png)

# Level 6 > 7
The password for the next level is stored somewhere on the server and has all of the following properties:owned by user bandit7, owned by group bandit6, and 33 bytes in size.  Breaking this exercise down, we have two parts to accomplish our goal:we must FIND the flag, and we must READ the flag.  The easiest way to get the flag is using the `find` command here.  I've been on a quest to include the helpful commands grep since I believe it's rather out of place in this exercise.  I think that because without a `*` operator, there's no way to use `grep` for this problem that I can find.  Grep requires you to already have certain information.  I tried loading a variable `n=bandit7` and grepping for the owner that way, then loading the *many* results into a text file and grepping for the answer there. Admittedly I used the method from level 5 > 6 to locate the correct directory just to see if I could grep my way to it but as of yet no luck. You may notice in my answer here I have `2>/dev/null` at the end.  This essentially dumps error messages instead of printing them to the terminal and makes everything cleaner looking.  I'll talk about this more later.

![image](https://user-images.githubusercontent.com/113439757/197827339-dfab789d-9810-4cad-91d3-7a5640f4d886.png)

# Level 7 > 8
"The password for the next level is stored in the file data.txt next to the word millionth" The useful commands are `man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd`. This is a fine place to employ grep if you are looking for the easiest route through the levels. 
![image](https://user-images.githubusercontent.com/113439757/197595900-a8bdda50-3492-4653-9a10-f7713b43d37c.png)

# Level 8 > 9
"The password for the next level is stored in the file data.txt and is the only line of text that occurs only once" Remeber `2>/dev/null`? The supplemental reading here goes into greater detail about how it works and what is happening behind the scenes.  I highly recommend it. `Sort` and `Uniq` are your friend in this exercise.  Ultimately we want to break the problem down into steps so that pipes can more effectively help us.  We need to organize, then reduce, then read the data to find our answer.  The inclusion of the archive and compression commands in the helpful commands section is to highlight the fact that they can be piped into other commands. 

![image](https://user-images.githubusercontent.com/113439757/197828564-16ba2553-227a-4d3f-acb3-bc48b3f1e78a.png)

# 9 > 10
"The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters."  We have an answer inside the prompt with the use of `strings`. We can leverage what we've already learned about the passwords presented so far in that they are 32 characters in length to craft the right command for the job.

![image](https://user-images.githubusercontent.com/113439757/197850603-28c5eaa0-43f5-41c6-b059-ec7688ea660f.png)

# 10 > 11
"The password for the next level is stored in the file data.txt, which contains base64 encoded data."
