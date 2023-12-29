---
title: "Ownership Problem With Git Solved"
date: 2023-05-25
url: /Ownership-Problem-with-Git-Solved/
description:
categories: [Commands]
draft: false
---
When we install windows fresh ownership of folders doesn't change in git. As a result it throws ownership error. Which is something like this: 

```
'E:/Example' is owned by: 
    'S-1-5-20-18634556-634524560-354234-1550' 
but the current user is: 
    'S-1-5-20-3264345-30432434-3373425-1033' 
To add an exception for this directory, call: 
git config --global --add safe.directory E:/Hugo/Sites/blog-site
```
This message indicates that the directory 'E:/Hugo/Sites/blog-site' is owned by a different user than the current user, and Git is warning you about potential permission issues.

If you want to add an exception for this directory, you can use the command suggested in the message:

```
git config --global --add safe.directory E:/Example
```

This command adds the specified directory to a list of safe directories that Git considers when detecting potential Git operations that may be unsafe.

Alternatively, if you are the owner of the directory, you can change the ownership of the directory to your current user using the following command in the terminal:

```
chown -R username:groupname E:/Example
```

Replace "username" with your current username and "groupname" with your current group name. This command recursively changes the ownership of all files and subdirectories in the specified directory to the specified user and group.

To change the ownership of the directory to your current user, you should use your PC's username. 

The group name is a collection of users who share the same permissions for a particular file or directory. By default, when a new user is created in Linux or Unix-based systems, a group with the same name as the user is also created.

You can use the `ls -l` command on Linux or Unix-based systems to view the owner and group of a directory. The output of this command will show you the owner and group of the directory, like this:

```
$ ls -l E:/Example
drwxr-xr-x  8 user1  staff  256 May 25 11:39 Example
```

In this example, the owner of the 'Example' directory is 'user1', and the group is 'staff'.

If you are using Windows, you can check the owner of a directory by right-clicking on the directory and selecting 'Properties'. Then, click on the 'Security' tab, and you'll see the current owner of the directory listed under the 'Group or user names' section.

To change the ownership of the directory to your current user, you can use the `takeown` command in the Windows command prompt. Here's an example command that changes the ownership of the 'E:/Hugo/Sites/blog-site' directory to the current user:

```
takeown /f E:/Hugo/Sites/blog-site /r /d y
```

This command recursively changes the ownership of all files and subdirectories in the specified directory to the current user. Make sure to use administrative privileges.