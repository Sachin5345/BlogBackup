---
title: "The Python application written using Django Framework!"
datePublished: Fri Mar 29 2024 12:25:31 GMT+0000 (Coordinated Universal Time)
cuid: clucmzsc2000008jz8a6a62c3
slug: the-python-application-written-using-django-framework
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711714834465/b9e3d739-1a4f-4bed-bb9e-61b93b527cd0.png
tags: python, django, backend,  vscode, applicationprograming, backendcode

---

I've wanted to use Python and the Django Framework to develop a backend application for a long time. So here I am.

# Concept of Django framework

A high-level Python web framework called Django makes it easier to create online applications quickly, cleanly, and scalable. By utilising the "batteries-included" concept, Django offers a comprehensive collection of tools and frameworks, freeing developers from having to start from scratch when building their application logic.  

# Benefits of Django

## Rapid Development

Object-Relational Mapping (ORM) databases, template engines, URL routing, authentication, and other built-in Django capabilities make development easier and enable developers to create applications more quickly.

## Scalability

Because Django is naturally scalable, developers can handle growing volumes of data and traffic without experiencing performance issues. Applications scale easily with its support for several deployment methods and flexible structure.

## Security

Web applications must be secure, and Django provides built-in defence against prevalent security risks including SQL injection, clickjacking, cross-site request forgery (CSRF), and cross-site scripting (XSS). Django also promotes best practices for handling data validation and user authentication.

## Versatility

Because of its versatility, Django may be used to create a vast array of applications, including social networks, APIs, e-commerce platforms, and content management systems. Because of its adaptability, developers can customise apps to satisfy particular business needs.

## Community and Ecosystem

Django boasts a vibrant and supportive community of developers who contribute to its ecosystem by creating reusable components, plugins, and packages. This wealth of resources makes it easier for developers to extend Django's functionality and address complex requirements effectively.

## Documentation and Support

Django provides thorough documentation that is an important tool for developers of all skill levels. Furthermore, the Django community ensures that developers have access to help whenever needed by means of forums, mailing lists, and online communities.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711704754651/03a1e450-6717-4e66-a58c-d8c1f6b9b0c3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711704782114/691c97fe-637b-4ec6-b440-a6eb4acadcea.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711704842286/98821c71-6c0d-429e-9677-f197f3a4e981.png align="center")

Let me tell you about the pre-requisites we need for this project:

> [VS Code (Visual Studio code as a IDE)](https://code.visualstudio.com/)
> 
> [Python](https://www.python.org/downloads/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705082084/59129d1a-0a6c-4185-a494-62f85be64ccf.png align="center")

Once you download these two and have it installed like any other software, all you need is the Django framework. Asking me where do you find that?

You can find all the instructions written in [Django Framework Documentation](https://www.djangoproject.com/download/).

But, since python is already on your machine, all you need is:

> pip install django

Once you run the above command in the terminal of the VS Code, here is what you get to see:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705275165/a204af5d-b2cc-408b-adc8-c219f17d03f7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705358357/7c2f57d7-5448-48f0-abcc-3dcf52c39ba3.png align="center")

Run "***<mark>django-admin startproject &lt;name of the application you would want to create&gt;</mark>***" to start creating the project or the application. Here I am creating an application called "ordernow". So my command will be:

> django-admin startproject ordernow

When I run this, I can see the ordernow folder created on the left side navigation pane:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705625183/3de1f42e-c231-41fe-aebc-f5669fb24abb.png align="center")

Just expand the pane to see it's components:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705708775/f4708002-643c-4938-8a4f-9a9fa1043451.png align="center")

Now since my project folder was different from where the prompt was, I did a cd &lt;foldername&gt;, which in my case was:

> cd ordernow

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711705993756/bedfa920-103c-4dc0-9b02-905eff5ba1a0.png align="center")

Once I was in the same directory, I had manage.py application code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706058132/df1e6305-6e2c-41d2-a179-a2c909604fcd.png align="center")

For now, understand this to be running as a simple server for you on the local machine. I wanted to understand how does this code display an output. So I ran the command below:

> python manage.py runserver

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706374572/61e745e3-b620-431f-a787-7fc72a20eff9.png align="center")

Let's check what this code displays:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706371082/077bc593-5a76-404a-ba93-3d03f8499c1e.png align="center")

Boom!! A simple webpage welcoming us to use Django framework.

Once you run the runserver command on the VSCode and start to see this webpage, the VSCode starts generating logs. To see how it reacts if I use a different port, I used 5000 as the port instead of 8000, meaning to say instead of using

> http://127.0.0.1:8000

I used

> http://127.0.0.1/5000

and here was the log:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706541384/8bafd6da-4522-4c7a-b357-e1d87dea7788.png align="center")

If you see the log in yellow colored font, it has this 404 at the end... meaning it did not reach the application at all. So changing the port back to 8000 got me a 200 status, which in web developer's language, is an OK status

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706633380/1bd4b879-39ba-4122-973d-144430518e4e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706919778/d36f5ad3-21d2-4a9b-aa38-342c749ee01a.png align="center")

# Creating the application

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711706990254/792ae0a6-5809-4ed6-a627-89f93143e24f.png align="center")

Since I wanted to create an application for books, I chose the app name as books

Here is what I used to create the application:

> django-admin startapp books

This command now creates a folder inside VSCode that has the name books and also provides the necessary files:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707127211/39371ee6-8134-47b5-89ea-6b40592b0017.png align="center")

If I have to reach an application on the web, it needs routes. So I configured another file under the books folder and named it urls.py

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707210925/f001f1f3-a63f-4090-9f35-898038d4389e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707298738/bc24616b-dd3a-4d04-94d5-3fa3d4c07f68.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707418369/0322fe37-0f38-4ed3-b9c2-5d444ff15625.png align="center")

Before we get there, we need to register/install our application. How do we do it? Navigate to the settings.py file under the ordernow folder, and scroll down to INSTALLED\_APPS section. Just add the name of your application over here. In my case this was books, so I added books.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707662390/b194dcb7-1c69-4378-b83f-52465177ec29.png align="center")

Include the paths of URL's now:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711707852995/2230452b-2941-495c-b77f-fad2b66f83c7.png align="center")

Since the server is running and it updates as you update the code, you can see the changes happening as and when you change the code.

I wanted to write a function/API that checks the health of my site and returns me a message. So I added this piece of code:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708028212/dd97f05c-a01c-4346-9e75-10dd115fb6c9.png align="center")

Once I did this, I could see the changes on the terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708080396/2a8d7dca-e60f-4023-8d46-60cf77528ab9.png align="center")

To check how the webpage was doing, I navigated to the URL once again, but with the route as /books/health :

> http://localhost:8000/books/health

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708151005/a6bb8e44-fba2-4bed-b603-c9a1eaa13806.png align="center")

The message that I had coded was returned back to me! Baby step 1 accomplished!

Before we plan the webpage we would need some metadata for the application that we are creating. I had these on my mind, so I created a Class called Inventory and added them under the models.py file hosted under books folder. Note that for every file we write there are some modules that we import. This is a basic need in python and is readily available to us with VsCode's intellisense.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708511340/976ce9f0-ba30-4546-a2b4-bd2d50cf747c.png align="center")

The next step was to start migrating this data into the server. Meaning, create a table into the database. So, I ran the command:

> python manage.py makemigrations

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708862879/4cb94cde-7fa3-4720-8bca-64cf8266a1b6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708883118/db361704-1c62-4e7e-b1bc-9636b9ad5bb3.png align="center")

While ***<mark>makemigrations</mark>*** was just a prepping step for the data entry into the table, there is another command that moves the data:

> python manage.py migrate

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708901952/890218f9-45d3-4da6-b92b-895f9da98b76.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708923981/7ab104bc-c543-47d3-a31b-5bf3115acde5.png align="center")

The next step was to modify this webpage with the admin prompt and create a superuser for performing the CRUD operations. I ran the command :

> python [manage.py](http://manage.py) createsuperuser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710817707/00f9967f-b7c0-4a8d-8619-7711bf2ad749.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711708953794/389dcf88-e8e3-4c55-97ea-5a3be6d97787.png align="center")

These credentials used do not resemble those of any real user and are used just for the project. So I decided to go with the GOAT Virat Kohli to be my superuser.

To test if this works, I hit the below URL:

> http://127.0.0.1:8000/admin

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711709098572/29b447c6-b746-45aa-809d-d2edb2abb6b9.png align="center")

There we have it!! The admin dashboard for our web application. Now this is basic. We need to enhance some features on this.

So, under the admin.py of the books folder, edit the code:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711709242795/ed7cc97c-7987-4f87-9ecc-a31b65395d76.png align="center")

Once the inventory is added through the code, check it on the webpage:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710199886/a7d20dc9-0f1c-427c-b88e-7334f722b40b.png align="center")

Great! That's success #2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710707956/b64b89d7-cfc8-4531-9cda-0fe1ffa43216.png align="center")

Let's add some inventory and check. I wanted to add one of my favorite books, so I added "Malgudi Days".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710266325/3c227629-f04d-4043-986f-b3abc91bccd4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710319979/bf351b89-0b2e-4270-9c0e-8db896687bd1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710914742/fbe760b3-d7a6-4836-b8c3-d188df1aba2b.png align="center")

Strange isn't it? The object got added, but the details do not show up. That is when it struck me that we need to add some display-related features to this code. So I navigated to the admin file again and wrote some more modifications;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710431659/9ec7e78a-bb2a-4957-ad94-7c2b626b9a9b.png align="center")

On checking this code modification now,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710478008/4b48b41e-f480-49de-a955-6fa23f11a35d.png align="center")

Booom!! There was a display with the content of the inventory. Great!! time to proceed one step ahead!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710626846/0e7b75d1-f92f-442a-8ace-66c7dee101a2.png align="center")

Let's create an API to get the list of books:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711710567480/92afb474-cfb9-4e44-ac4d-68b4ef089b7d.png align="center")

What did we do in the above step? We just created a function by name get\_books and initialized a list called results. Now, results is a blank list. We now have to iterate through every item under books and get the data to append it to the list.

Make sure to add the route as well:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711711208979/9b813433-d3b6-401b-83ba-d9b61ca5d5cf.png align="center")

When you run the server once again, there is a high chance of a webpage showing you "***<mark>In order to allow non-dict objects to be serialized set the sage parameter to false</mark>***" error. I will show you a fix for this as I learn it.

I made the below modification to the code:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711711279786/aca6b657-961e-4a0a-945e-f90374ff2472.png align="center")

Once I did this and went back to my server URL, I could see this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711711324179/618ce204-d8e7-434f-b065-45b752f3be93.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711711525032/17f93ab9-b07a-4094-8989-5ce9883092f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712048280/51a3d06f-8253-43ec-a317-11558aa845dd.png align="center")

# API Testing

For API testing, you can always go to POSTMAN. We can download the desktop version [from this page](https://www.postman.com/downloads/).

Create a new collection on the home page once you install the Postman tool. Create a new request and choose GET as the method.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712308911/61b7a872-1111-4bfd-9717-19a0df6e98a2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712328266/04636743-39da-4ba3-97e8-5230a1862d75.png align="center")

Once you see a success here, try to add an entry to the inventory. Select the POST method:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712398166/4856cc1f-1b1c-40fc-ac52-c7b8e05f09d0.png align="center")

Click on "SEND"

You should be able to see this on the console:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712478986/c3b5f89c-cbdb-4387-9bbf-1333018d6903.png align="center")

To get all the weird formatting removed, there is something called as csrf exempt which we can use. To use the csrf exempt, we need to first import it from django.views.decorators.csrf module. In this module we have a tool called json.loads. This json.loads basically formats the body of the request.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712627080/9ee1ff44-9245-49cf-aee3-86e24a535428.png align="center")

Resend the request from the website and you can see this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712633023/9298fd0a-1138-4ca2-b73e-46ff879e2273.png align="center")

I want the API to do a true and false case . So I added the conditions:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712720741/163b1e44-8141-45af-9ea9-a3836b05e66d.png align="center")

Once we test the API from postman, we can now refresh the website:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711712746253/f74056c9-595d-4d0d-9695-ca72c730cbe9.png align="center")

Boom!! There we have the application doing everything we request!

# Scope of the project

I have just demonstrated how we can add an entry to the inventory. Once you get rich in Python programming skills, you can implement the same for Remove, Update, and Delete operations as well.

Lastly, I would like to say that Coding is always about being creative and catering to customer needs. So happy learning!!