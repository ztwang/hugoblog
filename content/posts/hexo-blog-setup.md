---
title: Using Hexo To Setup A GitHub Page Blog 
---
[Hexo](https://hexo.io/) is a Node.js based blog framework. It is very simple to use. To start building your blog with Hexo, you just need to know some Javascript, CSS and Markdown, which is a widely-used lightweight markup language for formatting text. Well, let's start!

## Quick Start

### Setup

First, make sure you have the latest [Node.js](https://nodejs.org) installed.  

``` bash
$ node -v
v5.10.1

$ npm -v
3.8.3
```

Install Hexo as a global module:

``` bash
$ npm i -g hexo-cli
```

Initiate your blog folder `my-blog`:

``` bash
$ cd my-blog
$ hexo init
```

Now you can see your blog folder has been initiated with a default blog.  
Now open `_config.yml` to change some settings.

### Create a new post

``` bash
$ hexo new "My New Post"
```

To learn how to create a post, please check Hexo [Writing Documentation](https://hexo.io/docs/writing.html)  
To learn more about Markdown, there is a fantastic tutorial you should try: [Markdown Tutorial](http://www.markdowntutorial.com/)

### Test and Deploy

``` bash
$ hexo server # or `hexo s` to start the local server
$ hexo generate # or `hexo g` to generate static files
$ hexo deploy # or `hexo d` to deploy the blog
```

To deploy to GitHub pages please check Hexo [Deployment Documentation](https://hexo.io/docs/deployment.html)
