---
title: How did you make this blog?
comments: true
excerpt: |
  <br>
  A guide on how to make the same blog that I have.
tags:
  - Tutorial
categories:
  - [Domain, Blogging]
  - [Programming, Javascript, Hexo]
toc: true
---

There are many reasons to blog ({% post_link why-blog my reasons to start this blog %}) and {% post_link why-hexo Hexo seems like the best tool that I've found %} for the job.
In this post, I'm going to show you all the major steps to setting up a blog just like this.

## Basic setup

### Setting up a Hexo project

To get started with Hexo, make sure that you have [Node.js installed](https://nodejs.org/en/download/).
Next we'll use the [Node Package Manage (`npm`)](https://www.npmjs.com/) (included with Node.js) to install Hexo.
To install Hexo globally, you can use the following command, otherwise, see [Hexo's install documentation](https://hexo.io/docs/#Installation) for other install options.
```bash
npm install hexo-cli -g
```

After Hexo is installed globally, you can use Hexo to initialize a blog.
To do this, create an empty folder and then call `hexo init`.
```bash
mkdir my-blog
cd my-blog
hexo init
```

Afterwards, your directory will look like the following:
```
my-blog/
├── _config.landscape.yml     # a configuration file to extend the "landscape" theme
├── _config.yml               # the project's general configuration file
├── node_modules              # project dependencies installed by npm
├── package.json              # the approximate requirements of the project
├── package-lock.json         # the exact requirements of the project
├── scaffolds                 # your templates to build new posts off of
│   ├── draft.md
│   ├── page.md
│   └── post.md
├── source                    # this is where your posts and drafts will go
│   └── _posts
│       └── hello-world.m     # an example post
└── themes                    # hexo will look here for themes specified in _config.yml
```

TK discussion of changing title of blog in _config.yml and image in _config.landscape.yml

### Running a server

Let's get your blog up and running. First you need to start your hexo server:
```bash
# from the my-blog directory
hexo server
```
You should see the following message:
```bash
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000. Press Ctrl+C to stop.
```
Now, open a web browser and go to [http://localhost:4000](http://localhost:4000) to see your blog.

### Creating new posts

To add your first post, you can type the following:
```bash
hexo new post my-viral-post
```
If you refresh your web browser on [http://localhost:4000](http://localhost:4000), you should see your new blog post.

This new post lives in `source/_posts` and is called `my-viral-post.md`.
It's full path is `my-blog/source/_posts/my-viral-post.md`.
The `.md` at the end of `my-viral-post.md` stands for [Markdown](https://en.wikipedia.org/wiki/Markdown).
Markdown is marked up by Hexo into HTML.
This is nice because it is less work to write in Markdown than HTML.
If you're not familiar with Markdown, there are many resources online, including [this Markdown cheatsheet](https://www.markdownguide.org/cheat-sheet/).

TK discuss frontmatter and writing in markdown here

In addition to standard Markdown you can write your post in HTML directly or use [Hexo's tag-plugins](https://hexo.io/docs/tag-plugins).
I don't really use the tag-plugins, as I can do all the same things in Markdown, which I'm more familiar with.

If you make edits to the post, refresh the web browser to see your changes.

### Configuring your page

If you haven't already, open your new post in a text editor.
At its top, there's a special area area is called [_front-matter_](https://hexo.io/docs/front-matter.html).
For example, yours probably looks like this:

```
---
title: my-viral-post
date: 2021-01-14 19:45:16
tags:
---
```

This front matter is a list of variables that will be used in the post.
It is in [YAML](https://en.wikipedia.org/wiki/YAML) format and can also be formatted in [JSON](https://www.json.org/json-en.html) (YAML is probably easier).

There are several existing front-matter variables that you can use or you can create your own. 
If you make your own, they will be used in the layouts in your theme.
For example, [here is how `title` is used in the default `landscape` theme](https://github.com/hexojs/hexo-theme-landscape/blob/440617fd44eeafe4fa4d080b3536194812953c3e/layout/_partial/article.ejs#L8). 
If you want to see what front-matter variables already are supported you can see [Hexo's front-matter documentation](https://hexo.io/docs/front-matter).

Two front-matter variables that I use in addition to the ones above are `categories` and `excerpt`.
* `categories` are like tags, but allow nesting.
  For example, for a post using the Hexo Javascript library, you might have the categories be `Programming > Javascript > Hexo`.
* `excerpt` specifies text to be used instead of the full content of your post in the post's preview on the home page.
  This is nice because it makes it easier to scroll through your posts.
  Note that the `excerpt` is used directly as HTML, rather than being marked up from Markdown.

Here is an example of what your front-matter may look like.
```
---
title: My Viral Post
date: 2021-01-14 19:45:16
tags:
  - Tutorial
categories:
  - [Domain, Blogging]
  - [Programming, Javascript, Hexo]
excerpt: |
  <br>
  My excerpt that will be shown instead of the posts content on the blog's homepage.
---
```

### Hosting your blog on Github 

## More advanced setup
### Config settings
### Setting up Google Analytics
### Setting up comments with Disqus
### Modifying an existing theme

## Details glossed over
* Using images in Markdown
* Creating draft posts