---
title: "Mastering Linux File Permissions and Access Control Lists"
datePublished: Tue Jul 25 2023 13:42:52 GMT+0000 (Coordinated Universal Time)
cuid: clkicjzxm00010alea4se9zrr
slug: mastering-linux-file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690293309261/051e7584-5344-4905-8793-111d821f064d.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690293683211/350f225e-087e-4c58-b9c9-d2caae48978a.jpeg
tags: linux, security, trainwithshubham, tws, file-permissions-linux-unix-acls-access-control-lists-security-permissions-chmod-chown-setfacl-getfacl-octal-notation-symbolic-notation-user-permissions-group-permissions-other-permissions-fine-grained-access-control-file-ownership-file-system-security-command-line-operating-systems

---

# The legacy of the Linux commands

Following from the Day - 5 streaks of learning Linux commands and shell scripting, there is something really simple yet a must-have tool for any Linux user or administrator. The **man** command in the Linux operating system stands for "manual," and it is used to view the system's online reference manual pages. These manual pages explain in detail the numerous commands, system calls, library functions, and configuration files that are available on your Linux system. The man command is an essential tool for both new and seasoned users to quickly learn the functions and usage of various commands and utilities.

Let's quickly consult Ryan (our IT admin from the previous post) to understand the usage of this command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690258163868/084ce9b4-c267-4fe2-b0dc-cfe411f69fe0.png align="center")

The syntax for the man command is pretty simple:

**man \[section\_number\] &lt;command name&gt;**

While the section number is an optional component in the syntax, you can just write man &lt;command name&gt; as shown below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690259012083/c3f5117a-7925-4b4f-ad52-4d8a379d37d2.png align="center")

So, tell me, what does this do? **man** displays the manual for the command that we have asked for, outlining how to use it and what features are available.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690259274290/f2164f27-c8f8-4f2e-ad91-35b14448a515.png align="center")

If you look at the bottom of the highlighted screenshot, it asks if we want additional help; you can use 'h' for help, or if you discovered what you were looking for, you can exit the manual by pressing the 'q' button. A very handy and valuable tool in any Linux user's or administrator's toolset!!

# The File and Folder Permissions

After you've learned how to use the "man" command, I'd want to go over a separate but highly helpful idea called File Permissions and Access Lists. This function is essentially an identity and access management capability or a wonderful security solution for the files we work with under Linux.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690287668910/799bcec4-c266-4eb2-ad21-63cde3e5cdde.png align="center")

Hmmm... great to see these 3. But how do these three work with file permissions?

![Learning the shell - Lesson 9: Permissions](https://linuxcommand.org/images/file_permissions.png align="left")

While the file owner, group owner, and other users will all have 3\*3 file rights, the very first bit of the permission determines whether this is a file or a directory. If the first bit is 'd,' it means that the object we're looking at has directory rights; otherwise, it's a file.

Take a look at the below screenshot where there is a text file called "firstfile.txt" and there is a default directory ".ssh"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690284677565/05243b21-3cca-444c-be59-3ae8514afcfd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285205650/5b26a37e-1957-43fd-8fab-92629a1c2d9c.png align="center")

***PS: The screenshot was taken after the completion of this activity. Hence the file permissions are all modified.***

Alright! That gave us an idea of what can be the permissions and how we identify if the object we are looking at is a file or a directory. What next?

Let's run the "**ls -al**" command to see the permissions for the files and folders in the current working directory and look at the text file we have created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690284831346/065060d9-1f48-4531-8dce-ee86f178fbc4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690289437085/1b63cf7e-6b30-4f62-ae26-88328109a7a5.png align="center")

When I spoke to Ryan, I was determined to understand how I can set a read-only permission on the firstfile.txt

Indeed, he was kind and told me to run the chmod command with the first set enabled since I was the owner and I just needed the file to be read-only.

[Chmod Calculator](https://chmod-calculator.com/) can be of great help if you are new to calculating permissions.

Once I made my calculations and ran the chmod command, I wanted to verify if that command set the right permissions for the file. So I ran the ls -al command again and booooommmm!!! I was able to change the permissions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690284951423/23c49dd2-a1f8-4b64-bb4d-09e453ea8d40.png align="center")

Since the file was read-only I wanted to double-check if i actually understood what Ryan had gracefully taught me. So i tried changing the permissions now to read-write-execute for the file owner. That went well too!!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285020938/c064348d-f8bb-4950-ab8d-96261cd3e30c.png align="center")

Alright!! Now that we have all understood about the file permissions, it's time to understand two great commands from access control.

# Access Control Lists

* ## getfacl
    

In Linux, the getfacl tool displays the Access Control Lists (ACLs) of files and directories. ACLs go beyond the standard owner, group, and other permissions to provide a more granular mechanism to restrict access permissions. The getfacl command displays the additional permissions assigned to specified users and groups for a given file or directory.

***<mark>Syntax</mark>*<mark>: getfacl [options] [file/directory]</mark>**

Let's talk with an example and use our newly created firstfile for the exercise.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285501307/7353752e-009b-4c24-9b49-e300ac3e799d.png align="center")

The getfacl command returned me the name of the file, the owner, and the group as well. Along with these attributes, the command also displays the permissions respectively.

I am pretty sure you have the next question for me... Alright, what if I want to set the access control list? That's our next instruction.

* ## setfacl
    

In Linux, the **setfacl** command is used to configure Access Control Lists (ACLs) for files and directories. ACLs go beyond the typical owner, group, and others rights to provide a more fine-grained method of managing access permissions. Individual users and groups can be granted specified permissions on a file or directory using setfacl.

***<mark>Syntax: </mark>* <mark>setfacl [options] acl_spec file/directory</mark>**

Let's work out the setfacl command with the same firstfile and see how that works.

To understand the setting up of access control list for the current user which is ec2-user since this is linux on AWS, I will provide the access to the same user. Let's get that working on the terminal and look at what changes in the permissions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285568647/43b4fcdf-f7ff-4da1-9bf3-3e4aaea0f2da.png align="center")

With the setfacl command now properly executed without issues and also the permissions re-written, it is now time for us to see if the ACL for that file changed. So we know what's next on pipeline for us. Yes!!! you got that correct.. Run the getfacl command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285629708/3aa01430-77ca-4bb4-a5d4-1d3d94fc9706.png align="center")

That's amazing!! isn't it? Glad that there are so many ways to secure our files and access controls. Let me hand you a bonus tip... while ls -al gives me all the file permissions for all the files and folders, there is a "-ltr" switch that works great with ls command. This switch is a useful way to view files and directories, especially when you want to see the most recently modified ones at the bottom.

Here's a breakdown of the options used in the `ls -ltr` command:

* `l`: Displays the output in long format, providing detailed information about each file and directory. The long format includes file permissions, number of links, owner, group, file size, modification date, and filename.
    
* `t`: Sorts the output based on the modification time (timestamp) of the files and directories. The most recently modified files appear at the bottom of the list.
    
* `r`: Reverses the order of the sorting, so the oldest files appear at the top and the most recently modified files appear at the bottom.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690285721585/1e74c2ec-1d0e-4b1b-b96f-0400d89025ce.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690292274833/a8f2dd17-7262-4143-9cd0-4790edb8b00f.png align="center")

# Conclusion

Security of files and folders is a crucial part of the infrastructure. Especially when it is all about data security, these are lethal tools that can safeguard you as a first line of defense. Hopefully, I was able to convey how critical these are!

Happy Learning!