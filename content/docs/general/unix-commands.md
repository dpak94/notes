---
layout: post
title: UNIX Commands
weight: 1
url: /docs/general/unix-commands
---

# UNIX

- Cheatsheet [here]([Unix Commands Cheat Sheet: All the Commands You Need](https://www.stationx.net/unix-commands-cheat-sheet/))

## Commonly Used Commands

| **Command**                             | **Function**                                                                                          | **Command**                      | **Function**                                                                                                                    |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `echo Hola`                             | Outputs Hola                                                                                          | `man {command}`                  | Get manual information on the command                                                                                           |
| `echo hello > file.txt`                 | Saves the text *hello* to the file _file.txt_                                                         | `help {function}`                | Get help on the function                                                                                                        |
| `nano hello there > hola.txt`           | Multiple lines can be saved to the file *hola.txt* using **nano**                                     | `whatis {command}`               | Explains what a command is                                                                                                      |
| `cd -`                                  | Returns to previous directory                                                                         | `whereis {packageName}`          | Shows where a package is installed                                                                                              |
| `cd ~`                                  | Returns to Home Directory                                                                             | `uname -a`                       | Detailed UNIX system information                                                                                                |
| `ls -1`                                 | Lists all files and dirs line by line                                                                 | `halt`                           | Stop the system immediately                                                                                                     |
| `pwd`                                   | Present Working Directory                                                                             | `who`                            | Display who is logged in                                                                                                        |
| `touch fileName`                        | Creates an empty file called fileName                                                                 | `head -n 5 /etc/adduser.conf`    | Shows first 5 lines in file _adduser.conf_                                                                                      |
| `file banana.jpg`                       | Describes file content                                                                                | `tail -n 5 /etc/adduser.conf`    | Shows last 5 lines in file _adduser.conf_                                                                                       |
| `cat file1 file2`                       | Concatenates and display the content of files *file1* & _file2_                                       | `sudo unmount /media/disk`       | Unmount a disc from Linux                                                                                                       |
| `cat file.txt file2.txt > combined.txt` | Writes all the content from files *file.txt* & *file2.txt* into _combined.txt_                        | `mount /grp {diskName}`          | Confirms that the disc has successfully unmounted                                                                               |
| `history`                               | Prints out the most recently used commands. Execute the commands by typing `!{number-of-the-command}` | `cp -i fileX Docs/fileX`         | Overwrite a file with another file of same name. `-i` prompts you (interactive) before overwriting                              |
| `rm file1`                              | Removes file1                                                                                         | `cp -r Docs/ Downloads/pics/`    | Copies everything recursively in folder _Docs_ to folder _pics_                                                                 |
| `rmdir Docs`                            | Removes directory  _Docs_                                                                             | `mkdir -p books/hemmingway/favs` | Create a dir through sub-dirs                                                                                                   |
| `rm -f file2`                           | Force removes _file2_                                                                                 | `mv test submission`             | Changes the names or moves a directory file                                                                                     |
| `rm -i file3`                           | Interactive deletion. Asks you whether to remove the file or not                                      | `cmd1 \| cmd2`                   | is the pipe character; feeds the output of the command _cmd1_ and sends it to the command _cmd2_, e.g. `ps aux \| grep python3` |
| `rm -r Downloads`                       | Recursive Deletion. Deletes all the files in the dir _Downloads_                                      | `cmd > file`                     | Output of *cmd* is redirected to _file_. Overwrites pre-existing content in _file_                                              |
|                                         |                                                                                                       | `cmd >> file`                    | Output of *cmd* is appended to _file_                                                                                           |

![](https://www.stationx.net/wp-content/uploads/2022/11/unix-file-permissions-diagram.png)

---

## Pacman Commands

| **Command**                                           | **Function**                                                                                                                 |
| ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `sudo pacman mirrors`                                 | Checks the status of the mirros currently in the mirrorlist                                                                  |
| `sudo pacman-mirrors --fasttrack && sudo pacman -Syu` | Rewrites the local mirrorlist in descending order of download speed                                                          |
| `sudo pacman-mirrors --countrylist`                   | Gets a list of countries currently serving mirrors                                                                           |
| `sudo pacman-mirrors  --api --set-branch {branch}`    | Changes the branch between stable, testing or unstable. After changing the branch, rebuild the mirror list & update packages |
| `sudo pacman -Syuu`                                   | Downgrade the package while changing the branches                                                                            |
| `pacman-mirrors -G`                                   | Check which branch the machine is on                                                                                         |
| `pacman -Qtdq`                                        | Lists orphan packages                                                                                                        |
| `sudo pacman -Rns {package}`                          | Removes the package                                                                                                          |
