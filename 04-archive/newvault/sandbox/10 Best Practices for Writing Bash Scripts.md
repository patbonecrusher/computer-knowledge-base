---
creation date: 2024-11-04 13:30
tags:
  - dev/language/bash
  - shell/cli
  - references/best-of
---

```cardlink
url: https://medium.com/@talhakhalid101/10-best-practices-for-writing-bash-scripts-95d57e675939
title: "10 Best Practices for Writing Bash Scripts"
description: "Everyone who has come to this corner of mine, must for one reason or another, knows that I really like using the terminal, automating…"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:750/1*T8URQWaq7G2qhmi8_zu0wQ.jpeg
```

Everyone who has come to this corner of mine, must for one reason or another, knows that I really like using the terminal, automating “scripting” everything I can, including my current desktop system, which today is still i3wm. Well, for this task we use our beloved terminal, regardless of the shell you use, these tips will be useful. Definitely if you are new to GNU/Linux, then you will find yourself face to face with the bash shell.

A Bash Script is a file in which multiple shell commands are coded to perform a particular task, this article includes some healthy habits for writing a script, mainly to improve efficiency and make it more readable.

![](https://miro.medium.com/v2/resize:fit:1400/1*T8URQWaq7G2qhmi8_zu0wQ.jpeg)

# 1. Comment the code

Definitely something basic, but one that many forget and that is always very useful, either for yourself, or for others who want to review or modify your script, it is undoubtedly decisive in achieving clean code that can explain various parts of complex codes. While you are focused on writing the script, it is easy to get confused with the code you have written as time goes by. It is also effective when working in a group on a large project, as it helps you understand what the function or method actually does.

**_ALSO CHECKOUT:_**


```cardlink
url: https://medium.com/nerd-for-tech/error-handling-in-bash-scripting-b842133cd3d8?source=post_page-----95d57e675939--------------------------------
title: "Error handling in Bash scripting"
description: "Scripts are one of the key tools for a system administrator to handle a set of daily activities such as running backups, adding…"
host: medium.com
favicon: https://miro.medium.com/v2/5d8de952517e8160e40ef9841c781cdc14a5db313057fa3c3de41c6f5b494b19
image: https://miro.medium.com/v2/resize:fit:520/1*K6g_F6z54avoLZgjCoaMPw.jpeg
```


# 2. Using Functions

As you may know, a function is a set of commands grouped together to perform a specific task that helps to modulate the workflow, eliminating code repetition. It makes the code cleaner and more readable, as well as easier to maintain.

```bash
#!/bin/bash  
function check_root() {   
  echo "function has been called";   
}
```
# 3. Using double quotes

Using double quotes will help eliminate unnecessary globbing as well as word splitting, including whitespace, when variable values ​​contain a separator character or a whitespace.

# 4. Terminate execution on error

Sometimes, when running a script, there may be some execution error. Even if a command is not executed, the script may continue to run and affect the other commands in the script. To avoid further logical errors, we should include set -o errexit or set -e to terminate the command in case of error.

```bash
#!/bin/bash   
# Terminate script if error occurs   
set -o errexit
```
# 5. Declaring Variables

Declare the variable according to its data type and usage. When the variable is not declared, bash may not be able to execute the related command. Variables can be declared globally or locally in the script. For example:

```bash
#!/bin/bash   
# Variable declaration, as you note it is of variable=value format   
declare -r i=30  
function my_variable(){  
  local -r name="${HOME}"  
}
```
# 6. The use of keys

Bind variables with curly braces while using variable concatenation with strings to avoid unnecessary use of variables. This also helps to easily identify the variable while using it in a string. For example:

```bash
#!/bin/bash  
# Terminate the script if there is an error  
set -o errexit  
# Custom variable  
data="${USER}_data is being used"
```
# 7. Replacing the command

While assigning the output of the command to the variable, bash uses the command substitution feature. We need to use $() instead of backticks to assign the output to variables as recommended.

```bash
#!/bin/bash   
# Terminate the script if there is an error   
set -o errexit   
#Display the date   
date_now=$(date)
```
# 8. Variable Nomenclature

In our system, all environment variables are named using uppercase letters. So when we declare a local variable, we should declare it using lowercase letters to avoid conflicts between the environment and local variable name.

```bash
#!/bin/bash   
# Terminate script if error occurs   
set -o errexit   
ser_var="$HOME is your correct login."
```
# 9. Declaring Static Variables

If you have static data that remains unchanged throughout the script, you can assign the value to a static variable whose value cannot be modified. You can declare the static variable using the read-only command.

```bash
#!/bin/bash  
#Testing nginx configuration  
readonly test_conf_path="/etc/nginx/conf.d/test.conf"
```
# 10. Debugging

Debugging is the most essential part to identify a problem. We can check the syntax error of the script, so to check it we need to run the bash script with -n using the bash command.

```bash
$ bash -n script_name
```
Additionally, we can enable and run the script in debug mode using the following command.

```bash
$ bash -x script_name
```