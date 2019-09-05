# Command Line

Learning how to use the command line is the first step toward creating your new website.

## Why Developers Use the Command Line

When using a computer, it's common to use a mouse or touchpad to move the cursor to an icon, then click on the icon to communicate to the computer's operating system. This visual interface is called a graphical user interface (GUI). 

When developers use a computer, they often use the command line instead of the graphical user interface. Text commands can be typed into the command line to communicate directly with the computer's operating system. Not only is it faster to use the command line, but there are tasks that you can complete through a command line that you can't complete through a graphical user interface.

## Unix Versus Windows Shell

### Command Prompt

Command prompt symbols vary by operating system. This can be especially confusing to beginners. Of the three most common operating systems for web development, Linux and Mac OS X are Unix-based, while Microsoft has its own proprietary Windows operating system. The command prompts for Unix-based and Windows operating systems are different. Also, some of the commands are the same on both systems, and some aren't.

Unix command prompt

```shell
$
```

Windows command prompt

```shell
C:
```

## Caveats

### Command Line Prompt

We will be using ```$``` to indicate command prompt, but this will be operating system specific in reality.

### Carets

Throughout this tutorial, you might see a word or hyphenated words inside of caret symbols. This is a convention commonly used by developers in documentation to indicate that the carets and their contents should be replaced with a variable. A variable is a generic word or hyphenated words that store a value.

```shell
<variable>
```

## Commands

There are many possible commands that you can use. Fortunately, only a few come up most often and you can use these to get started.

Because you will be using a command line instead of graphical user interface, you will need to give commands to the computer's operating system to let it know where you are working within your computer folders and what action you want the operating system to take there. In addition to getting help when needed, many of the commands you will use most often will involve navigating, creating, and deleting folders and files via command line.

## Useful Unix Commands

### Help and Manual Pages

Show help info in your terminal, such as a list of commands

```shell
$ help
```

Show manual page for a specific command in your terminal

```shell
$ man <command-name>
```

Exit manual page

```shell
$ q
```

### Make Directory

Make a directory (folder)

```shell
$ mkdir <directory-name>
```

### Change Directory

Change directory

```shell
$ cd <directory-name>
```

Change directory back to the prior directory

```shell
$ cd ..
```

Change directory back to your home directory

```shell
$ cd
```

### List Files

See a list of the files in the directory you are in

```shell
$ ls
```
