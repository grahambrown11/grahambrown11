---
title: "Building a website with Hugo"
date: 2019-10-20
draft: false
menu: blog
weight: 1
---
When it comes to hosting a website there are many options - from using a database with a programming language that generates pages to hand editing pages or somewhere in-between.
<!--more-->
While creating html pages manually works, it can easily become a time consuming task. Keeping all the pages looking the same and adding common elements like a header or menu needs to be done on all the pages, in order to get around this some software programming can help. There are 2 popular ways to use programming: the one way is to generate the pages in a build process (also known as static website generators) that are uploaded to the server, the other is to generate each page at runtime on the server and optionally using a database as well - like Wordpress does.

Using the runtime generated approach has some downsides as it requires a few different pieces of software to run, like in the case of Wordpress: Apache, PHP and MySQL. Most hosting services provide these or even offer a similar service (Wix & SquareSpace) to host you website, and it doesn't cost a whole heap. Using static website generators also require software, but are much simpler - there is the software to build the site (usually on a local pc) and the server software like Apache. 

When it came to choosing an option for my website I decided to use the static website generator and host it on [GitHub Pages](https://pages.github.com/) (which is a free service from GitHub). The reason for the choice, besides the price, was that I am a developer and the workflow around static website generators is similar to my everyday workflow - edit, build/compile, commit/publish.

There are many popular static website generators and in particular these 2 generally float to the top of the popularity pile: [Jekyll](https://jekyllrb.com/) and [Hugo](https://gohugo.io/). I ended up choosing Hugo as it's simple - no dependencies, easy to install and run. I did not spend hours making a choice, I read some comparisons and decided to give Hugo a try and found it worked for me so I stuck with it.
