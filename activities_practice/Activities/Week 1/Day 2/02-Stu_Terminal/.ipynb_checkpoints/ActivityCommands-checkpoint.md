# File System Operations

It's time to try out the command line for yourself. In this activity, you will use the command line, or terminal, to perform common file system operations.

## Instructions

Complete the following steps using the command line:

  1. Open Terminal (Mac) or Git Bash (Windows).

  2. Check your current working directory.

$ pwd


  3. Navigate to your desktop.

$ cd ~/desktop


  4. Confirm that your current working directory is the desktop.
Use pwd

  5. Create a folder called `Pets`.
$ mkdir Pets

  6. Navigate into the `Pets` folder.
$ cd Pets

  7. Inside `Pets`, create two folders: `Dogs` and `Cats`.
$ mkdir Dogs Cats

  8. Navigate into the `Cats` folder.
$ cd Cats

  9. Create a file named `name.txt` and insert the text `My name is Lucky! Bark!`. Then save the file.

$ touch name.txt

Vi name.txt
Press I key on your keyboard( this should enable INSERT mode on the command line. Check the last line on your command line  screen should display 'INSERT')

Type the text suggested
Press escape key on your keyboard ( may need to press twice on macbook. Check last line on your command line screen should not display INSERT anymore)
Type :wq (this should save and exit)

  10. Read the file `name.txt` and output the results to the console.
$ cat name.txt

  11. Navigate back to the root of the `Pets` folder.
$ cd .. 
 

  1. Copy the file `name.txt` into the `Dogs` folder.
$ cd Cats  ( navigate to Cats folder)
$ ls ( check list of files , should display name.txt)
$ cp name.txt /c/Users/61452/Desktop/Pets/Dogs  ( need to provide source file name with extension followed by path of the destination folder)
$ cd .. ( navigates back to Pets folder)
$ cd Dogs ( navigates to Dogs folder
$ ls ( check list of files, name.txt should be available now

  12. Delete the `Cats` folder and its contents.
$ cd .. ( navigates back to Pets folder) 
Use pwd to check if you are in Pets folder
Use ls to check if both Cats and Dogs folders are available
$ rm -r Cats
Use ls to check only  Dogs folder is now available


  13. Rename the folder `Dogs` to `Lucky`.
Use ls to check Dogs folder is available
$ mv Dogs Lucky
Use ls to check folder is renamed


  14. List the contents of the root of the `Pets` folder.

Use ls

## Hints

* Use the [CommonCommands.md](Unsolved/CommonCommands.md) file for reference if you need help performing these file system operations.

* Use the `mv` operation to rename files or folders.

---

© 2021 Trilogy Education Services