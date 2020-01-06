<!-- learn echo and printf -->

# Hello World

A `shell script` is a file containing one or more commands that you would type on the command line.


## the code itself.

The code itself is nothing more then 3 words, one commend and 2 arguments that it is getting: 

```sh
echo Hello, World!
```

### Some Monir Decissions

Before you turn that code into a script, you need to make two decisions: **_what will you call the script_** and **_where you will put it_**.

#### Naming the script:

As you can already guess from initial questioned asked, naming the script can be a trick task. for example, it might be an error to call the script `test`, due to a fact that the test is a shell built-in.

```sh
[que@core]$ type test
test is a shell builtin
[que@core]$ type -a test
test is a shell builtin
test is /usr/bin/test
```
Typically, Unix command names are as short as possible. They are often the first two consonants of a descriptive word (for example, mv for move or ls for list) or the first letters of a descriptive phrase.

Many shell developers add a suffix, such as `.sh`,to indicate that the program is a shell script. The script doesn’t need it, and I use one only for programs that are being developed. The suffix is `-sh`, and when the program is finished, I'd  suggest remove it. A shell script becomes another command and doesn’t need to be distinguished from any other type of command.

#### Directory for the Script:

When the shell is given the name of a command to execute, it looks for that name in the directories listed in the `PATH` variable. This variable contains a colon-separated list of directories that contain executable commands.
directories that contain executable commands. This is a typical value for $PATH `:/bin:/usr/bin:/usr/local/bin:/home/.local/bin`

As such, you iwsh to run your script from shell, you must place it under PATH or edit PATH to reach your script by editing the PATH.
Commands are usually stored in directories named `bin`, and a user’s personal programs are stored in a `bin` subdirectory in the $HOME directory. To create that directory, use this command:

```sh
[que@core] mkdir $HOME/bin
```

Now that it exists, it must be added to the PATH variable:

```sh
[que@core]PATH=$PATH:$HOME/bin
```

For this change to be applied to every shell you open, add it to a file that the shell will source when it is invoked. This will be .bash_profile, .bashrc, or .profile depending on how bash is invoked. These files are sourced only for interactive shells, not for scripts.

### Creating the script and running it

Creating shell script is not that  different from creating any other simple files. You can set it with `vim` or `nano` terminal editors. Although we'd suggest to use specific template for shell, python or ruby scripts according to their suffix.

To do so, we'd suggest to generate a template at your home directory `vim ~/.vim/sh_header.temp` and in the file write down the header for the script:

```sh
#!/usr/bin/env bash
# set -xe
#########################################################
#Scripting name :
#Purpose        :
#Args           : adding
#Created by     : your nickname
#E-mail         : name@mail.com
#Version        : 1.0.0
#########################################################
```
and once that's done configure our vim to handle your files with `.sh` suffix. To do so add the next line to `vimrc` file in your home directory. 

```sh
filetype indent on
filetype plugin on
syntax on

au bufnewfile *.sh 0r /home/$USER/.vim/sh_header.temp
```
Where:

`au` – means autocmd
`bufnewfile` – event for opening a file that doesn’t exist for editing.
`*.sh` – consider all files with .sh extension

so to conclude, after generating a file and adding in to it, script commands with `hw` script at `/home/que/bin` folder:

```sh
#!/usr/bin/env bash
# set -xe
#########################################################
#Scripting name :
#Purpose        :
#Args           : adding
#Created by     : your nickname
#E-mail         : name@mail.com
#Version        : 1.0.0
#########################################################

echo Hello, world!
```
That works, but it’s not entirely satisfactory. You want to be able to type hw, without having to precede it with bash, and have the command executed. To do that, give the file execute permissions: `chmod +x bin/hw` .Now the command can be run using just its name:

```sh
[que@core]$ hw
Hello, world!

```

### Building better scripts.

When writing scripts, one must take into considiration, different specs:
- modularity : your scripts should be built in a way,  that will make easy to edit them.
- expressiveness : variables and function names should be usefull.
- extansibility : invoking your scripts should be by you and by others(users, groups, scripts) as well.

In that manner our script can be upgraded in next manner:


```sh
#!/usr/bin/env bash
# set -xe
#########################################################
#Scripting name :
#Purpose        :
#Args           : adding
#Created by     : your nickname
#E-mail         : name@mail.com
#Version        : 1.1.1
#########################################################
msg_hello="Hello, World!"

printf "%s\n" "$msg_hello" !"
```

Mind that version number was advanceds due to minor and misc changes in code.


## Exercises
1. Write a script that creates a directory called bpl inside $HOME.Populate this directory with two subdirectories, bin andscripts.
2. Write a script to create the “Hello, World!” script, hw,in $HOME/bpl/bin/; make it executable; and then execute it.