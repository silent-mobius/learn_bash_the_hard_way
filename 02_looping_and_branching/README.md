<!--for while until select loops and alike-->
# Conditionas and Loops that come with it

## Before all the tools

### Exit Status

In previous chapter we talked about [Special Character](../Exercises/01_in_out_and_through/README.md)

At the heart of any programming language are `condition check`  and `loop iteration` execution. 

- Condition check execution is making a choice between two or more actions, one of which may be to do nothing, based on a condition.
- Loop iteration is the repetition of a section of code until a condition changes.

There several types of conditional execution: 

- `if then fi`
- `case esac`
- `&&` and `||` which mean logical AND and logical OR operators.
  
With the exception of for and case, the exit status of a command controls the behavior.

You can test the success of a command directly using the shell keywords `while, until,and if` or with the control operators `&&` and `||`.
The exit code is stored in the special parameter `$?`. If the command executed successfully (or true), the value of `$?` is zero. If thecommand failed for some reason, `$?` will contain a positive integer between 1 and 255,inclusive.
A failed command usually returns 1. Zero and non-zero exit codes are also known as `true` and `false`, respectively.
A command may fail because of a syntax error:

```sh
[que@core] $ printf "%v\n"
bash: printf: 'v': invalid format character
[que@core]$ echo $?
1
```

Alternatively, failure may be the result of the command not being able to accomplish it's task:

```sh
[que@core]$ mkdir /qwerty
bash: mkdir: cannot create directory '/qwerty': Permission denied
[que@core]$ echo $?
[que@core]$ 1
```


In the shell, there are three main types of loop:

- `while CONDITION;do ;done`
- `until CONDITION;do; done`
- `for iterators in DATA; do  ;done`



