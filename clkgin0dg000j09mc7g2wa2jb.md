---
title: "Leveraging Examples to Harness the Limitless Potential of Linux Day-4 #90DaysofDevOps"
datePublished: Mon Jul 24 2023 06:57:38 GMT+0000 (Coordinated Universal Time)
cuid: clkgin0dg000j09mc7g2wa2jb
slug: leveraging-examples-to-harness-the-limitless-potential-of-linux-day-4-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690050450141/5085daa1-782e-4fa3-bb3a-7723a3e582ed.jpeg
tags: blogging, linux, shell-scripting, trainwithshubham, tws

---

# The commands continue...

Whatever stage of your Linux experience, learning shell scripting can significantly increase your productivity and efficiency. With the help of shell scripts, you may automate a variety of chores and optimize your workflow because they are compact yet mighty programs written in the shell language that carry out a series of commands in sequential order. To help you understand the principles and put them to use in actual situations, we'll walk you through the fundamentals of shell scripting in this blog.

We can set aliases for the commands to make things simpler while you run the code. Let's see a conversation between Ryan and Sharon (our imaginary colleagues from the IT teams):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690176358375/4858b4b6-ae7b-4ead-b85c-8562c13c7935.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690176430382/c7c65098-12a0-4b27-925d-802af0315859.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690176449663/ebd95b69-5588-43ae-8380-779172815e7a.png align="center")

So while Sharon wanted to talk to Ryan and understand how the alias command works, Ryan quickly spun up his VM on the AWS machine with the Linux OS and then:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690176522669/983ef5af-cdc9-45d6-9259-66ab2a7671d5.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690176723575/0475a540-75a3-46fb-b8d3-c52fb0a39c98.png align="center")

and then...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690177070536/fd947584-22f1-4ce4-89a3-9b3fc71a7c97.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690177831861/f831de66-2f79-4aae-a275-dcb51b1ae270.png align="center")

# Understanding Shell Scripting

To understand how shell scripting works, I have created a simple file called "greeter" with an extension ".sh" specifying that it is a shell script

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690178410696/1536eb0d-1b41-4e7e-8d98-00e3a088c7a4.png align="center")

Let's see the permissions for this file and also make sure that we have enough permissions to execute this script.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690178538543/a0ad2776-859c-4af1-9325-99e91bb56cc5.png align="center")

The ls -al command clearly shows that there is no executable permission for the script that we just created. Let's change the same with the chmod command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690178654468/6001fa15-9c70-41dc-ac2d-6d08f02187c1.png align="center")

Boom!!! The file now has executable permission... let's see how it behaves when we execute it from the terminal:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690178813615/cc7713ba-be39-45b6-92e8-910632b8df0b.png align="center")

Good enough!! That was the first achievement in shell scripting... We now wrote a simple script that displayed us "Hello, World!". Wasn't that pretty simple? Let's now see if we can make it a bit more interesting and instead of just displaying just a "Hello, World!" message if it can check and greet a user.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690180891165/b5a9774d-a7e0-455a-bffe-3cf26ab6078f.png align="center")

You may ask me where is step 2 in the screenshot... Simple that is the creation of the script using the vim editor... Here is a snip of the script:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690181044587/a85b6c37-a09f-4325-8aba-1208b9b7a1a7.png align="center")

Now, the script was working fine when I said the name "Sandeep" (matching case). Let's quickly attempt something else and see what may be returned as the output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690181166539/e1d1c698-4c29-49e8-9529-1adea78dda48.png align="center")

# **Conclusion**

Let's turn to Ryan (remember? our IT guy on the top of this page) and see what has got to say.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690181512187/1d0130ea-9817-4090-ae07-a242b59f49b9.png align="center")

While I have tried my best to show you what can be the usage of shell scripting, how it is written and what can it do... there are endless possibilities and endless combinations of commands. Get creative and start exploring the possibilities. Happy learning!!