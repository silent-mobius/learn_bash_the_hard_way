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

Many shell programmers add a suffix, such as `.sh`,to indicate that the program is a shell script. The script doesn’t need it, and I use one only for programs that are being developed. My suffix is `-sh`, and when the program is finished, I'd  suggest remove it. A shell script becomes another command and doesn’t need to be distinguished from any other type of command.

#### Directory for the Script:

When the shell is given the name of a command to execute, it looks for that name in thedirectories listed in the PATH variable. This variable contains a colon-separated list of directories that contain executable commands.