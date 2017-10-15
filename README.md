# Moving Files
An assignment designed to challenge students to move files and clone repositories on the command line. The WATS3030 course uses [Digital Ocean](https://digitalocean.com) as the chosen hosting service. The challenge and instructions here are written according to how Digital Ocean works, but you can accomplish the same goals using any server running Unix or Linux. Be aware that different distributions of Linux are not identical, so some details (such as the package management tool) may vary accordingly.

## Base Requirements
The base requirements for this assignment are to complete the following list of tasks and then commit your repository back up to the server. Your completion of these tasks provides evidence of your success. You will create, delete, move and rename files and folders in several ways.

To begin working on this project, you will need to set up a new server:

1. Create an account on [Digital Ocean](https://digitalocean.com).
2. Create a new Droplet with the following configuration:
  * Ubuntu (the latest version)
  * You do not need to select any particular App.
  * Be sure to **add your SSH key** by clicking the "Add SSH Key" link (or selecting your previously added SSH Key) near the bottom of the Droplet creation form.
3. Connect to your Droplet via SSH. ([Consult this guide for more detailed help with SSH Keys and access.](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets))
--I titled my Droplet "Droplet1.0"

Once you have created your Droplet and successfully connected to it, you will need to install and configure Git:

1. Install Git on your Droplet using `apt-get`, which is a package management tool used by Ubuntu.
  * Run the command `sudo apt-get install git` to begin the install process
  * Pay attention: `apt-get` will ask you to confirm that you want to install the application once it determines how much disk space it will take up. You will have to press `Y` to continue the installation.
  * You will know the installation is finished when you see: `'git help -a' and 'git help -g' lists available subcommands and some concept guides. See 'git help <command>' or 'git help <concept>' to read about a specific subcommand or concept.`
2. Configure the basic global variables in Git:
  * Run the command: `git config --global user.name "Your Name"`
  * Run the command: `git config --global user.email "you@youremail.com"`
  * Run the command `git config --list` to see that these values have been successfully set. You should see a list that indicates your name and email address correctly.
--I was able to do this, but I made an error when typing and accidentally added some unnecessary text to the directory. Eventually I would like to learn how to clean it up, but for right now the information is all there. 
`user.name=Carly
user.email=casdarcher@gmail.com'
git config --global user.email casdarcher@gmail.com
git config --global user.email casdarcher@gmail.com
git config --global user.email "casdarcher@gmail.com"
git config --global user.name "Carly"
pwd
exit
x
root@Droplet1:~# git config --global user.email "casdarcher@gmail.com
root@Droplet1:~# `

Now that you have Git installed on your Droplet, you must configure Github to allow this Droplet to access your repositories. That means you must add the Droplet's SSH key to your Github profile so Github knows you are using this machine. But since your Droplet is brand new, you must first generate an SSH key for this Droplet.

1. Follow the Github Guide to [Generating SSH Keys (Linux)](https://help.github.com/articles/generating-ssh-keys/#platform-linux) to generate an SSH key for your Droplet and add it to your Github profile.
2. Now that you have added the SSH Key to your Github profile, fork the [WATS1030 Moving Files](https://github.com/suwebdev/wats1030-moving-files/) source repository into your personal Github account.
3. Verify that you have been successful by copying the SSH Clone URL from your repository homepage and cloning the repository using command-line Git: `git clone <SSH ClONE URL>`
  * Please note: You should be in your home directory (`cd ~`) when you do this.
4. Change directory into the repository root directory.
--I found Fernando's video really helpful for this process. When I change back to my repository root directory I see `/root`

Congratulations! You have successfully provisioned a brand new virtual server (aka "Droplet") and cloned a Git repository so you can work with those files on your Droplet. This is a great accomplishment! But we have more to explore.

Now that you have this repository on your Droplet, we will perform some file management exercises to explore how to create, copy, move, delete, upload and download files on your server. These steps all use the files and directory structure contained beneath the `challenge_files` directory.

1. Change directory into the `challenge_files` directory.
--It took me a while to figure out that the root directory is different from the wats1030-moving-files directory. Once I figured that out I was quickly able to `cd` down into the challenge_files directory.

2. Use the `cp` command to copy `index.html` to `index.html.bak` (Note: This is a common naming convention when you wish to back up a file.)
--deleteme.html  delete_this_directory  img  index.html  index.html.bak  logs

3. Use the `mkdir` command to make the directory `tmp/` inside of `challenge_files`.
--deleteme.html  delete_this_directory  img  index.html  index.html.bak  logs  tmp

4. Use the `cp` command to copy `index.html` to `tmp/keepme.html`.
--/root/wats1030-moving-files/challenge_files/tmp
-- After I run a `ls` command I know see the `keepme.html` listed in the tmp folder

5. Use the `rm` command to remove (or "delete") the file `deleteme.html`.
--Before I run the command 
`deleteme.html          img         index.html.bak  tmp
delete_this_directory  index.html  logs`
--After I run the command
`delete_this_directory  img  index.html  index.html.bak  logs  tmp`

6. Use the `rmdir` command to remove (or "delete") the directory `delete_this_directory/`. Does it work? Figure out how to remove `delete_this_directory/` and all the contents within.
--I got the following error on my first try `rmdir: failed to remove 'delete_this_directory/': Directory not empty`
--I used the rm -R delete_this_directory to remove the directory and all the content

7. Use the `scp` (SSH secure copy) command to upload an image to the `img/` directory. (`scp <your_filename.jpg> root@<YOUR DROPLET IP ADDRESS>:~/wats1030-moving-files/challenge_files/img/`)
  * Make your life a little easier by uploading a file that isn't too huge in filesize.
  * You may upload any file you choose; please keep it appropriate for the classroom/workplace.
  * You may use an application such as WinSCP or Cyberduck if you choose.
--By opening a different Terminal window I was able to use the command above to upload an image into the proper location  
  
8. Use the `mv` (move) command to sort the `challenge_files/logs/` directory.
  * Use `mkdir` to create new directories to store the files.
  * Organize the new directories into year and month.
  * Use `mv` to move the log files into their appropriate directory.
  * Hint: Use wildcards to move several files at a time so the work goes much more quickly.
--This was definitely the most difficult part of the assigment for me. I learned that it matters where is the directory you are when trying to move files. I ultimately was able to use `mv 2015-01* 2015-01/.` to move all the files. 
--When I run a `ls` in the logs directory I know see this 
`2015-01  2015-03  2015-05  2015-07  2015-09  2015-11
2015-02  2015-04  2015-06  2015-08  2015-10  2015-12`
  
Once you have completed this work, you should `commit` your changes and `push` them back up to Github. To do that, use the command-line Git application:

1. Change directory to the repository root directory (probably `~/wats1030-moving-files/`).
2. Run `git status` to see the current status of your repository. 
3. Run `git add -A` to add all of your changes to the repository.
4. Run `git rm <filename>` to tell Git that you have removed a file or directory (you should see prompts about doing this if you run `git status` again).
5. Run `git status` and notice how all of your altered files show up highlighted green in the "staging" area, and there should be no more files highlighted red in the "unstaged" area.
6. Once you've staged all your changes, you must make a `commit`: `git commit -m "Completed moving files assignment"`
7. After you have made your commit, you should push your changes to Github, which is the `origin` for your repository: `git push origin`
8. Review the response and make sure your `push` was successful.

Congratulations! You have now committed and pushed your changes to Github, all from the command line. This whole process may have seemed difficult or arduous at first, but with practice it becomes much faster to manage these files and commits via the command-line rather than most graphical tools.

## Stretch Requirements
The following goals are meant to provide more of a challenge for individuals who like that sort of thing.

* Create a Droplet using a different kind of Linux and repeat all of the above (altering your process according to the difference of tools/environment).
* Figure out how to connect to your Droplet using SFTP or a different file management/upload tool. (Or, if you used a GUI application before, then try it using only the command line.)
