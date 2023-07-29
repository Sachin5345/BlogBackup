---
title: "Commanding the OS with tasks"
datePublished: Tue Jul 18 2023 13:35:38 GMT+0000 (Coordinated Universal Time)
cuid: clk8c7qdn000009mfen1ee680
slug: commanding-the-os-with-tasks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689664684823/b3638433-ba10-4c9e-8ebb-b3c680c86e52.jpeg
tags: 90daysofdevops, trainwithshubham, tws, codewriting, thelinuxterminal

---

Running commands on the Linux terminal allows you to interface with your operating system and do numerous activities easily. The terminal, often known as the command line or shell, is a text-based interface that allows you to communicate with the computer's operating system by typing commands rather than using a graphical user interface (GUI).

Let's dive into some sample commands and see how tasks are accomplished:

## **<mark>Task - 1</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665361503/452ab93e-aa62-419c-a67d-e240e66da0ad.png align="center")

Solution: Run the **<mark>clear </mark>** command on the terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665446461/6abf8732-2382-4f15-83ce-9b0be55c07cc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665480034/d6dd75da-0967-40dc-b71f-8df5f1ca9ffa.png align="center")

## **<mark>Task - 2</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665567361/0d1aa656-04c7-4a8b-8fa1-4eeb5f3bc40a.png align="center")

Solution: Run the **<mark>pwd </mark>** command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665805480/89ad05c3-a2b8-4a7b-a083-3ebc468cb485.png align="center")

## <mark>Task - 3</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672016355/6e3a831b-92e7-4884-a4cf-41fa2ee19481.png align="center")

Solution: Run the <mark>mkdir devops </mark> command first and then run ls to see if the directory was created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672066299/82cb22e1-a110-4ea7-af68-e85d2191ed83.png align="center")

## **<mark>Task - 4</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672306266/8f4a44d9-f69a-47bf-91a2-128ecaa8e987.png align="center")

Solution: Run the cd devops first if you are in a home directory and then run the touch command to create the file in the devops directory so below are the three commands to run:

1. <mark>cd devops</mark>
    
2. <mark>touch firstfile.txt</mark>
    
3. <mark>ls</mark>
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672447981/383dfd4a-ca42-4d23-92d1-1dcb08148062.png align="center")

## **<mark>Task - 5</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672928808/1b2f1b46-51e5-4963-9120-2cb6d3d4b795.png align="center")

Solution: First perform the directory check if you are in the devops directory using the pwd command. Once this is confirmed, you can now perform the file creation using the touch command. The touch {&lt;start#&gt;..&lt;end#&gt;} command creates the desired number of files. The series of commands to execute are as follows:

1. <mark>pwd</mark>
    
2. <mark>touch file{1..10}.txt</mark>
    
3. <mark>ls</mark>
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672830132/0cc31b34-799d-4fe4-8fab-7b359e060a00.png align="center")

## **<mark>Task - 6</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689684375925/d1f76472-74d8-4a5b-b21b-d36210ea8be0.png align="center")

Solution: To create nested directories, you can run the command mkdir command with a "-p" switch. Now, if we just use ls, this will show us the one folder that has been created and that holds the rest of the folders within. But the command "tree", shows us the nested folders created.

PS: You may additionally need to run the commands to use the command tree if you are using Linux or any of its flavors for practice on the AWS console. I had to run sudo yum install tree" which made the tree command available for me on the Linux machine I was using for practice. The series of commands are as follows:

1. <mark>mkdir -p Folder1/Folder2/Folder3/</mark>
    
2. <mark>sudo yum install tree</mark> (depends on the flavor, for Linux it will be yum install, ubuntu would be apt install etc..)
    
3. <mark>tree</mark>
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689684348517/6af07579-9517-46c4-9ceb-9d6f4db66568.png align="center")

## **<mark>Task - 7</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685016478/a15c1f00-6de1-4fa6-91a8-12261ffb91b0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685277948/f331947e-7a14-4b39-a13d-8ad9ebc64f5c.png align="center")

Solution: First use the touch command to create the file. Once created, use the vim &lt;filename&gt; to edit this file. Press "i" to enter the insert mode, once done use the "esc" button from the keyboard alongside ":wq". This should save the edit and close the file. Finally, to check if this has succeded, you can execute "cat &lt;filename&gt;" to read the contents of the file on the console.

Below are the series of commands:

1. <mark>touch newfile.txt</mark>
    
2. <mark>vim newfile.txt</mark>
    
3. <mark>i</mark> (for inserting the content)
    
4. This is a test file to understand the commands.
    
5. <mark>"esc"</mark> (button from keyboard) <mark>:wq</mark>
    
6. <mark>cat newfile.txt</mark>
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685835504/cef4dfc8-4813-4c1e-b7e3-eb5a99bb371b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685773645/f4080362-3e7d-4379-a836-1934326464f8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685903406/177abb2f-caf8-4273-b93a-10bae5afe3ee.png align="center")

## **<mark>Task - 8</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689686570607/28c9b692-59b0-4098-a86c-b797fb9f28c1.png align="center")

Solution: first run the command ls -al which gives the list of all the files and permissions to the file. Review the information mentioned [in this article](https://www.redhat.com/sysadmin/linux-file-permissions-explained) to understand what number can be used. Now once you decide, use the chmod command to change the file permissions. Now use the same ls -al command to verify on the changed permissions. I wanted to change the file permissions to read-only here, so I have used 400. Here is a set of commands to execute the request from the user:

1. <mark>ls -al</mark>
    
2. <mark>chmod 400 newfile.txt</mark>
    
3. <mark>ls -al</mark>
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689686064738/e9c5aa7a-ca71-406a-ad1d-33a67ab43d1c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689686154712/2ea5a35d-ad5d-4633-9cd4-edb71cc74170.png align="center")

Though this was a small demo of what the commands can do, I am pretty sure this blog was interesting to read and understand how the terminal in an OS can be a game changer.

# **<mark>Conclusion</mark>**

Running commands on Linux can ease our tasks and reduce the time consumption needed to execute the commands manually.

More commands to follow and more illustrations to follow in the next blog! Wait for it!

Happy learning!