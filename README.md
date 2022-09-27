# Over-The-Wire
Over the wire guided tutorials
The wargames offered by the OverTheWire community can help teach and practice security concepts in the form of fun-filled games.  Bandit is recommended for absolute beginners.  If you've never opened linux before but you're interested in security this can help you get there.  To level up to one and capture the metaphorical flag, usually a string of random characters, you must SSH or log into the game server.  SSH stands for Secure Socket Shell or Secure Shell, and to learn how to syntactically arrange all our information to log in can be found in the manual by typing
![image](https://user-images.githubusercontent.com/113439757/191986004-a2976887-85a8-4a23-92ee-8d2d74c9992e.png)
It will then show you a list of all the correct syntax for common options
![image](https://user-images.githubusercontent.com/113439757/191985509-a83eedc1-3f19-4733-8008-3d689eed8991.png)
Judging from this, and the information given on the website we need to invoke ssh input the user@serverlocation and the port number since they want a connection on the nonstandard port 2220.
It should look like this ![image](https://user-images.githubusercontent.com/113439757/191988132-848d4dbf-09bd-4519-a602-6fba05079392.png).  After that, you'll have to enter the password for the server (bandit0) supplied on the website. Congratulations, you are now level 1.

Level 1 > 2
Use the same method to log into level 1 as you did level 0. The instructions state "The password for the next level is stored in a file called readme located in the home directory."  We have some hint commands available to us on the level goals page too which are pwd, ls, cat, cd, du, file, and find.  After logging in, you can see what directory you are in at any given time with the command "pwd" without quotes.  Pwd stands for print working directory.  We can also look at the contents of the directory using "ls" which stands for list directory contents and it will show us information about the files.
