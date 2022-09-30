## Over-The-Wire
Over the wire guided tutorials
The wargames offered by the OverTheWire community can help teach and practice security concepts in the form of fun-filled games.  Bandit is recommended for absolute beginners.  If you've never opened linux before but you're interested in security this can help you get there.  To level up to one and capture the metaphorical flag, usually a string of random characters, you must SSH or log into the game server.  SSH stands for Secure Socket Shell or Secure Shell, and to learn how to syntactically arrange all our information to log in can be found in the manual by typing `man ssh`.  It will then show you a list of all the correct syntax for common options
![image](https://user-images.githubusercontent.com/113439757/191985509-a83eedc1-3f19-4733-8008-3d689eed8991.png)
Judging from this, and the information given on the website we need to invoke ssh input the user@serverlocation and the port number since they want a connection on the nonstandard port 2220.
It should look like this `ssh bandit0@bandit.labs.overthewire.org -p 2220`.  After that, you'll have to enter the password for the server (bandit0) supplied on the website. Congratulations!

# Level 0 > 1
Now that you are logged in, the instructions state "The password for the next level is stored in a file called readme located in the home directory."  We have some hint commands available to us on the level goals page too which are pwd, ls, cat, cd, du, file, and find.  After logging in, you can see what directory you are in at any given time with the command `pwd`.  Pwd stands for print working directory.  Typing this command we can see we are already in the home directory, so the readme file should be here.  We can also look at the contents of the directory using `ls` which stands for list directory contents and it will show us information about the files. We can type the command to confirm this.  To print the contents of the file we use the `cat` command followed by the filename as written when we typed ls and we have our answer.

![image](https://user-images.githubusercontent.com/113439757/192812957-bc034ea8-086b-4817-addd-fa91b2f5b940.png)

Are there other ways to arrive at our answer? Absolutely! The one above is probably the most beginner friendly, but if you know already how to tie commands together with the pipe symbol `|` then you could also do something like `find * | cat *` to arrive at the same answer for this specific situation.  The same would apply to `file -f readme`,  `head readme` or `awk '{print $1}' readme`.  Learning multiple ways to perform a task is critical to enhancing literacy and articulating specificity! 
![image](https://user-images.githubusercontent.com/113439757/192873847-73cb4bf9-428a-46ee-b8ed-d348cd545a37.png)


# Level 1 > 2
Use the same method to log into level 1 as you did level 0. The directions are "The password for the next level is stored in a file called - located in the home directory" and the helpful commands are the same as before.  Now we have helpful reading material as well; specifically http://tldp.org/LDP/abs/html/special-chars.html which is a guide to special characters in bash scripts.  Knowing that our instructions are similar in format to the previous quesiton, so too should then our investigation be conducted.  Gathering information is the first step, so we need to find out what folder we are dumped in after login. we use `pwd` and it tells us that we are in the home directory where we need to be. From there we can use `ls` to see our folder - is present.
