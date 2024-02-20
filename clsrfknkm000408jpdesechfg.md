---
title: ""Mastering Bash: Essential Tips and Tricks for Shell Scripting Success""
seoTitle: ""How to Optimize Your Shell Scripting Efficiency : Tips and Tricks""
seoDescription: ""Unlock the Power of Shell Scripting: Dive into the World of Automation and Efficiency! Explore beginner-friendly tutorials, advanced tips, and practical ex"
datePublished: Sun Feb 18 2024 11:34:56 GMT+0000 (Coordinated Universal Time)
cuid: clsrfknkm000408jpdesechfg
slug: mastering-bash-essential-tips-and-tricks-for-shell-scripting-success
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708452808898/a8adbcd8-21e3-49a9-ae44-8c69e18f3162.webp
tags: linux, bash, automation, devops, script, shell-script

---

### What is Shell Scripting?

A shell script is a script written for a command-line shell, which is a user interface for access to an operating system's services. Shell scripts allow users to automate tasks, execute sequences of commands, and perform various operations within the shell environment.

### types of shells.

Bourne shell

C shell

Bash shell

Korn shell

Z shell

### Why do we need shell scripts?

1. To avoid repetitive work and automation
    

2\. System admins use shell scripting for routine backups.

3\. System monitoring

4\. Adding new functionality to the shell etc.

### ***Examples:***

### How to send email alerts ?

script checks the available free RAM on the system, and if it's less than or equal to 700 MB, it sends a warning email to the specified email address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252424279/8c3b78f4-afc6-477b-8a76-fc749d26ea5c.png align="center")

When you run this script, it will check the available RAM and send an email if the free size is less than 700 MB. Make sure that your system has the `sendmail` command configured correctly to send emails.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708248611581/73e99b06-248a-4da9-bfa8-0a190794bd70.png align="center")

### Automate Server Inventory using Shell Script

This script collects information about the server, such as the server name, IP address, uptime, and OS type, and then stores this information in a CSV file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252456843/b526f4a8-ac48-474c-8580-94a122b4d9c6.png align="center")

When you run this script, it will collect the server information and store it in the `csv_file` in CSV format.

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708248813533/6354d33e-5b98-4d51-bb7f-d6abab65b2cd.png align="center")

### Working with PS1 Prompt Environment Variable

Display username, hostname and current working directory in the prompt

* \\u – Username
    
* \\h – Hostname
    
* \\w – Full path of the current working directory
    

This command will display the current value of the PS1 variable, which represents your Bash prompt configuration.

```plaintext
 echo "$PS1"
```

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708247181597/5f7127cc-936d-46d1-a508-3031b367b413.png align="center")

custom prompt for your shell

```plaintext
PS1="[\t ==>\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "
```

***output:***

`[\t ==>`: This part includes the current time (`\t`) followed by the string `==>`

`PS1` to this value, your shell prompt will include the current time, the string `==>`, the username, hostname, working directory, and whether the user is running as root or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708247471680/fd47659c-a057-4e90-89a2-a919115bc2d4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708247638033/f4894874-242e-4084-a865-867d67e2bab8.png align="center")

This setup will display the prompt with a red color for the time, a red color for the window title, and the username, hostname, and working directory in default color.

```plaintext
PS1="[\[\e[0;31m\]\t ==> \[\e]0;31m\]\u@\h: \w\a]\u@\h:\w\$ "
```

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708247859820/3ce68f82-b94d-49f0-898d-1a74e3ab70d8.png align="center")

***options:***

* \\a an ASCII bell character (07)
    
* \\d the date in “Weekday Month Date” format (e.g., “Tue May 26″)
    
* \\D{format} – the format is passed to sift time (3) and the result is inserted into the prompt string; an empty format results in a locale-specific time representation. The braces are required
    
* \\e an ASCII escape character (033)
    
* \\h the hostname up to the first part
    
* \\H the hostname
    
* \\j the number of jobs currently managed by the shell
    
* \\l the base name of the shell’s terminal device name
    
* \\n newline
    
* \\r carriage return
    
* \\s the name of the shell, the base name of $0 (the portion following the final slash)
    
* \\t the current time in 24-hour HH:MM:SS format
    
* \\T the current time in 12-hour HH:MM:SS format
    
* \\@ the current time in 12-hour am/pm format
    
* \\A the current time in 24-hour HH:MM format
    
* \\u the username of the current user
    
* \\v the version of bash (e.g., 2.00)
    
* \\V the release of bash, version + patch level (e.g., 2.00.0)
    
* \\w the current working directory, with $HOME abbreviated with a tilde
    
* \\W the base name of the current working directory, with $HOME abbreviated with a tilde
    
* \\! the history number of this command
    
* \\# the command number of this command
    
* $ if the effective UID is 0, a #, otherwise a $
    
* \\nnn the character corresponding to the octal number nnn
    
* \\ a backslash
    
* \\\[ begin a sequence of non-printing characters, which could be used to embed a terminal control sequence into the prompt
    
* \\e\[ – Indicates the beginning of color prompt
    
* x;ym – Indicates color code. Use the color code values mentioned below.
    
* \\e\[m – indicates the end of color prompt
    

### how to write and execute shell script ? simple shell script to install tomcat

```plaintext
#!/bin/bash

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.85/bin/apache-tomcat-9.0.85.tar.gz

tar -xvf  apache-tomcat-9.0.85.tar.gz

rm  apache-tomcat-9.0.85.tar.gz

mv apache-tomcat-9.0.85/ tomcat9
```

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708250320589/1f01fdf8-e1c1-4fcd-90c3-5eeb9a78aa8d.png align="center")

\=============================================================

### how to run user defined shell script as a system command ? (free ram size in MB)

root@ip:~# `vim`[`free.sh`](http://free.sh)

```plaintext
#!/bin/bash

free -m | awk 'NR==2{print $4 "MB" }'
```

root@ip~# `chmod +x`[`free.sh`](http://free.sh)

root@ip:~# `./`[`free.sh`](http://free.sh)

183MB

**OR**

root@ip:~# `pwd`

/root

root@ip:~# `/root/free.sh`

183MB

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708250603540/c199530a-4172-432d-b4d4-96eb3c95c6a1.png align="center")

\=============================================================

### check the path of file or command

root@ip:~# `which ls`

/usr/bin/ls

root@ip:~# `which cp`

/usr/bin/cp

root@ip:~# `echo $PATH`

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:**/snap/bin**

### How to change file path

**Move the file to**`/snap/bin/`

root@ip:~#`mv`[`free.sh`](http://free.sh)`/snap/bin/`

***without using ( ./ ) run file name***

root@ip:~# [`free.sh`](http://free.sh)

374MB

***without using ( .sh )***

root@ip:~# `cd /snap/bin/`

root@ip:/snap/bin# `ls`[`free.sh`](http://free.sh)

root@ip:/snap/bin# `mv`[`free.sh`](http://free.sh)`freem`

***return to home location***

root@ip:/snap/bin# `cd`

***run only file name***

root@ip:~# `freem`

374MB

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708250947186/19b90bc5-37f7-4349-b3c0-7954e761e302.png align="center")

\=============================================================

### how to change the temporary execute PATH

root@ip:~# `mkdir new_directory`

root@ip:~# `ls`

*<mark>new_directory</mark>*

***move the file***

root@ip:~# `mv /snap/bin/freem new_directory/`

root@ip:~# `cd new_directory/`

root@ip:~/new\_directory# `ls`

freem

***check the file PATH***

root@ip:~/new\_directory# `pwd`

/root/new\_director

### change the temporary execute PATH

```plaintext
 
export PATH=${PATH}:/root/new_directory
```

***run from any location in your terminal without specifying the full path to the file***.

root@ip:~# `freem`

183MB

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708251232941/3cda1834-d683-4410-b740-6d25130186dc.png align="center")

\=============================================================

### how to change the permanent execute PATH

This command displays all files and directories, including hidden

root@ip:~# `ls -a`

. .. .bash\_history .bashrc .profile .ssh

root@ip:~# `vim .profile`

```plaintext
 export PATH="$PATH:/root/new_directory"
```

***:wq! —-save file***

source a shell configuration file like `.profile` to apply changes made to them,

root@ip:~# `source .profile`

root@ip:~# `freem`

374MB

root@ip:~# `echo $PATH` /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:`/root/new_directory`

\=============================================================

### echo command :

***echo command to display command output***

advanced syntax of echo command : `echo [option] string /$variable/$(command)`

option : `\n ----line , \t ---tab space , \c ---cut next word ,`

Examples:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708251533108/b7229ec0-dadc-4248-bba4-1a4abf347b73.png align="center")

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

| colors | FG | BG |
| --- | --- | --- |
| black | 30 | 40 |
| red | 31 | 41 |
| green | 32 | 42 |
| yellow | 33 | 43 |
| blue | 34 | 44 |
| Magenta | 35 | 45 |
| cyan | 36 | 46 |
| wight | 37 | 47 |

### *syntax :*

```plaintext
#\e: This is the escape character.
#42: Sets the background color to green.
#33: Sets the text color to yellow.

echo -e "\e[42;33m vaibhav"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708251705393/8c1cbfd2-871f-43d6-85f4-091caf838a3b.png align="center")

### small script

root@ip:~# `vim`[`hello.sh`](http://hello.sh)

```plaintext
 #!/bin/bash

#\e[0m: This ANSI escape sequence resets the text attributes to their default values.

echo -e "\e[1;34mWelcome to my blog!\e[0m"
```

root@ip:~# `chmod +x`[`hello.sh`](http://hello.sh)

root@ip:~# `./`[`hello.sh`](http://hello.sh)

*Welcome to my blog!*

\=============================================================

### quotes:

***using single quotes output :***

root@ip-:~# `echo '$(ls)'`

$(ls)

***using double quotes output :***

root@ip-:~# `echo "$(ls)"`

[*hello.sh*](http://hello.sh)

*new\_directory*

***using non quotes output :***

root@ip-:~# `echo $(ls)`

[hello.sh](http://hello.sh) new\_directory snap

\=============================================================

### comments :

***use single line comment*** : #

***use multi line comment*** : &lt;&lt; myname

myname

```plaintext
<<myname
\e: This is the escape character.
42: Sets the background color to green.
33: Sets the text color to yellow.
myname
echo -e "\e[42;33m vaibhav"
```

\=============================================================

### variables 😀

A shell variable is a character string in a shell that `stores` some value. It could be an `integer, filename, string,` or some shell command itself.

\*\*Rule :*the name of a variable can only contain letters (*`a to z or A to Z`*) , number (*`0 to 9`*) , and the underscore character*`(_)`

```plaintext
#!/bin/bash
echo "variables"
x=10
y=20
z=30
echo "value of x: $x"
echo "value of y: $y"
echo "value of z: $z"
```

***OR***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252612455/dee95c9e-f2e2-4dcc-afe8-dc5ac300747b.png align="center")

***Output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708251905680/8a0247f3-a3c6-453f-8f15-37ec7810df3b.png align="center")

### Different types of variables like:

***user defined variables:***

root@ip:~# `x=10`

root@ip:~# `echo "$x"`

10

***system defined variables:***

root@ip-:~# `echo "$SHELL”`

/bin/bash

root@ip-:~# `env` #---------show all system defined variables

***special variables:***

root@ip-:~# `echo $?`

0

\=============================================================

### input & output command

\*\*\*echo :\*\*\**output command*

\*\*\*read :\*\*\**input command*

simple way 😀:

```plaintext
#!/bin/bash
var=$(systemctl status apache2 | awk 'NR==3 { print $2 }')
echo "your apache2 servers is : $var"
var1=$(systemctl status nginx | awk 'NR==3 { print $2 }')
echo "your apache2 nginx is : $var1"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252229493/10b2ccab-c774-4f5c-84b9-66d45670f308.png align="center")

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252198022/2bb98814-05bd-47d6-a4d3-7a620af02e0c.png align="center")

\==================================

### read command :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252924227/49816ef0-52da-4992-a695-325be00c08e4.png align="center")

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708252951660/508455dd-6f7e-407b-a22e-6e93d0efb0f9.png align="center")

\=============================================================

### Advance:

```plaintext
#!/bin/bash

# Prompt the user to enter the server name
read -p "enter your server name " web_sv

# Use systemctl status to get the status of the specified service and extract the status using awk
var1=$(systemctl status $web_sv | awk 'NR==3 { print $2 }')

# Print the status of the service with formatting
echo -e "your apache2 $web_sv is :\e[31m$var1\e[0m "
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708253100478/51e7f6b0-b826-473b-97a5-6e3ccd5e65e9.png align="center")

***\============================================================***

### how to providing input command line arguments

```plaintext
#!/bin/bash
read -p "first value v1:" v1
read -p "secand value v2 :" v2

result= $(expr $v1 + $v2)
echo "addition of $v1 and $v2 is : $result"
```

***output:***

*first value v1: 1*

*second value v2 : 2*

*addition of 1 and 2 : 3*

```plaintext
#!/bin/bash
v1=$1
v2=$2
result= $(expr $v1 + $v2)
echo "addition of $v1 and $v2 is : $result"
```

***output:***

ubuntu@ip-172-31-86-128:~$ `./input_command 5 6`

*addition of 5 and 6 : 11*

### \==========================================

### Decision Control statements of Shell Scripting

*By using conditional statements like if statement, elif statement and else statement,*

***Syntax :***

if \[ \[condition \] \]

then

statement

fi

***Example:***

```plaintext
#!/bin/bash
a=$#
 #checks if the value of the variable a is equal to 3.
if [ $a -eq 3 ]; then
 v1=$1
 v2=$2
 v3=$3
 result=$(expr $v1 + $v2 + $v3)
 echo "Addition of $v1 and $v2 & $v3 is: $result"
fi
```

***output:***

ubuntu@ip-172-31-86-128:~$ `./ if_condition 3 4 4`

*Addition of 3 and 4 & 4 is: 11*

***Example:***

*Your script seems to provide options to start, stop, and check the status of the Apache2 service based on user input*

*This script now correctly handles the user input for starting, stopping, and checking the status of the Apache2 service, and it displays appropriate messages.*

```plaintext
#!/bin/bash
read -p "select service action start and stop : " action
if [ "$action" == "start" ]
then
 sudo systemctl start apache2 
 echo "please wait....."
 echo "apache2 service start"
fi
if [ "$action" == "stop" ]
then
 sudo systemctl stop apache2
 echo "please wait....."
 echo "apache2 service stop"
fi
if [ "$action" == "status" ]
then
 sudo systemctl status apache2
 echo "please wait....."
 echo "apache2 service status show "
fi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708253403574/c44ad906-fcbb-49ff-94b6-026dedfbba47.png align="center")

\=============================================================

### what is a Loop ?

*some time we need to execute the same code several time*

***following types***

`The while loop`

`The for loop`

`The until loop`

`The select loop`

### `for` statement in Shell Script in Linux

The for loop operates on lists of items. It repeats a set of commands

*Syntax:*

```plaintext
#!/bin/bash
for var in $(seq 1 10)
do
echo "welcome to shell scripting "
echo " i am vaibhav "
done
```

### \==========================================

### Shell Scripting Generate or Print Range of Numbers ( Sequence of Numbers for Loop )

The syntax is as follows:

1. *seq LAST*
    
2. *seq FIRST LAST*
    
3. *seq FIRST INCREMENT LAST*
    

***Examples:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708253627202/859fc104-3685-4d0c-8fcf-8fe0f8482ade.png align="center")

***Examples:***

*Your script is a simple Bash script that prints "Welcome" followed by the iteration number, for 5 iterations.*

```plaintext
#!/bin/bash
for i in $(seq 5)
do
echo "Welcome $i times"
done
```

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708253753287/9c0b5747-2cfc-43ec-a312-a5ff7b29d207.png align="center")

### Using bash brace expansion in shell scripting to generate sequence of numbers

root@ip-:~# `echo {1..3}`

***output:***

1 2 3

***Examples:***

When you run this script, it will produce the same output as before: "Welcome 1 times." through "Welcome 5 times." each on a separate line.

```plaintext
#!/bin/bash
for ((a=1; a <= 5 ; a++))
do
echo "Welcome $a times."
done
```

`for ((a=1; a <= 5 ; a++))`: This line sets up a C-style for loop. It initializes the variable `a` to 1, specifies the condition `a <= 5` for continuing the loop, and increments `a` by 1 after each iteration.

***output :***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708253839956/d3d55acd-2e03-45c0-b503-6667e72d7c38.png align="center")

\============================================================

### while loop

*while loop is used to execute a set of commands repeatedly as long as a specified condition is true.*

***syntax:***

while \[ condition \]

do

\# Commands to execute

done

***Examples:***

`while` loop to print the value of a counter variable from 1 to 5. Here's a breakdown of each part:

`while [ $counter -le 5 ]`: This line starts a `while` loop that continues as long as the value of the `counter` variable is less than or equal to 5.

`((counter++))`: This line increments the value of the `counter` variable by 1

```plaintext
#!/bin/bash
counter=1
while [ $counter -le 5 ]
do
 echo "Counter is: $counter"
 ((counter++)) # Increment the counter
done
```

***output :***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708254008236/98b8c631-656c-47d3-8e7f-44ce5e6347d8.png align="center")

### *Reading a file with a while loop*

root@ip-:~# `echo "my name is vaibhav " > temp.txt`

root@ip-:~# `vim`[`while.sh`](http://while.sh)

```plaintext
#!/usr/bin/bash

# This line assigns the filename "temp.txt" to the variable file.
file="temp.txt"

# while loop that reads each line from the file specified by the variable file
while read -r line;
do

# echo $line: This line echoes (prints) the contents of the variable line
echo $line

# < "$file" instructs Bash to redirect the contents of the file specified by the variable $file as
#input to the while loop.

done < "$file"
```

When you run this script, it will read each line from the "temp.txt" file and print it to the console. If "temp.txt" contains:

***output :***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708254392213/1b802a96-28a9-41a4-82bc-669cb1568fae.png align="center")

### ***Examples:***

### **Writing to a file using a while loop**

script prompts the user to enter content into a file named "wh.txt" and then continuously reads input from the user until they press Ctrl+D (indicating end-of-file). Each line of input is then appended to the file. Here's a breakdown of the script:

```plaintext
#! /bin/bash
file=wh.txt
echo “Enter the content into the file $file”
while read line
do
#This line appends the content of each line read from the user to the file specified by the variable $file
echo $line >> $file
done
```

***output :***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708254617120/4ce48006-1e41-4070-9f58-2c0001f64d37.png align="center")

\=============================================================

### Infinite while loop

```plaintext
#!/bin/bash
while :
do
echo “An Infinite loop”
done
```

```plaintext
# We can press Ctrl + C to exit the script
```

\=============================================================

### select loop

select loop in Bash is used to create simple text-based menus in scripts. It allows users to choose from a list of options presented to them.

***Syntax:***

```plaintext
Syntax:
#!/bin/bash
select myVariable in variable1 variable2 ... variableN
do
case myVariable in
variable1)
 executed command
;;
 variable2)
 executed command
;; 
break
;;
*) echo "Invalid selection"
esac
done
```

***Example:***

script provides a menu for selecting a department (CS, IT, ECE, EE)

```plaintext
#!/bin/bash
select department in CS IT ECE EE Quit
do
case $department in
CS)
echo "I am from CS department."
;;
IT)
echo "I am from IT department."
;;
ECE)
echo "I am from ECE department."
;;
EE)
echo "I am from EE department."
;;
Quit)
echo "Exiting..."
break
;;
*) echo "Invalid selection"
;;
esac
done
```

* `select department in CS IT ECE EE Quit`: This line presents a menu with options: CS, IT, ECE, EE, and Quit. The user can select one of these options.
    
* `case $department in ... esac`: This construct checks the value of the variable `$department` and executes the corresponding block of code based on the selected department.
    
* `CS)` ... `IT)` ... `ECE)` ... `EE)`: These are the cases for each department. They echo a message indicating the selected department.
    
* `Quit)`: This case handles the option to quit. It echoes a message and then exits the loop using `break`.
    
* `*)`: This is the default case, executed when the user selects an option that doesn't match any of the defined cases. It echoes an "Invalid selection" message.
    
* `esac`: This keyword marks the end of the `case` construct.
    

```plaintext
output:
root@ip-172-31-86-128:~# ./hello.sh 
1) CS
2) IT
3) ECE
4) EE
5) Quit
#? 1
I am from CS department.
#? 4
I am from EE department.
#? 2
I am from IT department.
#? 7
Invalid selection
#? 5
Exiting..
```

***Example:***

script is a simple calculator program that allows users to perform addition, subtraction, and multiplication operations on two numbers. Here's a breakdown of how it works:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708255160588/32165525-9813-4486-a7b3-e2bfb93a16d2.png align="center")

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708255121345/cc046f1e-d2cc-4771-bfb6-a08bce2811bd.png align="center")

\=============================================================

### Until Loop :

The Until loop is used to iterate over a block of commands until the required condition is false.

***Example:***

```plaintext
#!/bin/bash
i=0
until [[ $i -eq 5 ]]
do
 echo "$i"
 ((i++))
done
```

***output:***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708254735352/fae7fc09-cc96-4731-bff6-c8a5aed6fc41.png align="center")