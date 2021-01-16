---
title: How did you make this blog?
tags:
  - Tutorial
categories:
  - - Domain
    - Blogging
  - - Programming
    - Javascript
    - Hexo
comments: true
excerpt: |
  <br>
  A tutorial on how to make a similar blog in Hexo.
toc: true
date: 2021-01-15 22:22:59
---

![](using-hexo-banner.jpg)

There are many reasons to blog ({% post_link why-blog my reasons to start this blog %}) and {% post_link why-hexo Hexo seems like the best tool %} that I've found for the job.
In this post, I'm going to show you all the major steps to setting up a blog just like this.
If you like this post and are interested in more like it, let me know in the comments below.

## Getting started with Hexo

### Installing Hexo

To get started with Hexo, make sure that you have [Node.js installed](https://nodejs.org/en/download/).
Next, we'll use the [Node Package Manage (`npm`)](https://www.npmjs.com/) (included with Node.js) to install Hexo.
To install Hexo globally, you can use the following command, otherwise, see [Hexo's install documentation](https://hexo.io/docs/#Installation) for other install options.
```bash
npm install hexo-cli -g
```

### Creating a Hexo project

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

<!--
TK discussion of changing title of blog in _config.yml and image in _config.landscape.yml
-->

### Viewing your blog locally

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

## Blog posts

### Your first post

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

<!--
TK discuss frontmatter and writing in markdown here
-->

In addition to standard Markdown you can write your post in HTML directly or use [Hexo's tag-plugins](https://hexo.io/docs/tag-plugins).
I don't really use the tag-plugins, as I can do all the same things in Markdown, which I'm more familiar with.

If you make edits to the post, refresh the web browser to see your changes.

### Front-matter

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

## Hosting your blog on Github 

Now that your blog is up and running, you may running how to make it available on the internet.
The easiest way that I'm aware of is to use [Github Pages](https://pages.github.com/) and [Github Actions](https://github.com/features/actions).
Github Pages lets you host a static website on Github;
  while Github Actions allows you to use Hexo to generate the static web pages that will be used.
(Creating the static pages is done behind the scenes when you run `hexo server`.
You can see what is generated by running `hexo generate` and looking in the `public folder`.)

To host your website, there are three steps:
1. Create a repository for your blog on Github
1. Setup your Github Action
1. Upload your blog to Github
1. Enable Github Pages

### Create a repository for your blog on Github

[Github](https://github.com/) is a website for storing code, among other things, that primarily uses [Git version control](https://git-scm.com/).
First, make sure that you have a [Github account](https://docs.github.com/en/github/getting-started-with-github/signing-up-for-a-new-github-account).
Then [create a repository](https://docs.github.com/en/github/getting-started-with-github/create-a-repo) for your blog.

Once you create your repository you should update your project's `url` and `root` in `_config.yml` in the following way:
```yaml
url: https://<github username>.github.io/<repository name>
root: /<repository name>/
```

For example, for this blog, I use the following, where my username is `audrow` and my blog's repository is called `blog`:
```yaml
url: https://audrow.github.io/blog
root: /blog/
```

If you're using this blog for your personal website you could do the following, but then your repository would have to be named `<your username>.github.io`:
```yaml
url: https://<your username>.github.io/
root: /
```

### Setup your Github Action

The Github Action that we are going to create has one purpose: generate the static pages somewhere that Github Pages can access it.
To generate the static pages, we're going to use the `hexo generate` command.
And then we're going to save those generated files to another Git branch.

I see two main reasons to store the generated files on another branch:
1. Storing generated files clutter up the differences between Git commits, which makes it hard to understand what has changed and bloats the branch, making it slower to download.
1. By using Github Actions, we can make updating the static files automatic each time you send new changes to Github.
   This way you don't have to remember to manually update the static files after changing something in your blog.

To create our action, we just need to create a [YAML](https://en.wikipedia.org/wiki/YAML) file in `my-blog/.github/workflows`.
(Note that the `.` in front of `.github` makes the directory by default hidden.
 On Linux and Mac, you can use `ls -a` to see that it's there.)

Now let's make the file:
```bash
# from the my-blog directory
mkdir -p .github/workflows # make directories
cd .github/workflows       # go into the new directories
vim pages.yml              # create a file with your favorite text editor
```

Then copy the following content into your `pages.yml` file:
```yaml
name: Pages

on:
  push:
    branches:
      - main

jobs:
  pages:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js 12.x
        uses: actions/setup-node@v1
        with:
          node-version: "12.x"
      - name: Cache NPM dependencies
        uses: actions/cache@v2
        with:
          path: node_modules
          key: ${{ runner.OS }}-npm-cache
          restore-keys: |
            ${{ runner.OS }}-npm-cache
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
          publish_branch: gh-pages
```

A couple things to note:
* This assumes that your working branch is named `main`.
  If it is not, feel free to change it.
* `npm run build` calls `hexo generate`, which generates the static files.
  You can see this by looking in your project's `package.json` file.


### Upload your blog to Github

The easiest way to setup your repository with Github is probably the following:
1. Make sure that you have [Git installed](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). You can check by typing `git --version` in your terminal; if you get an error, you should install Git.
1. Initialize your project with Git: top-level of your project (`my-blog`), run `git init`.
1. Change your branch to `main`, rather than Git's default of `master`, since this is Github's default:
   ```bash
   git checkout -b main
   ```
1. Tell your repository about your project on Github. You can just copy the project's URL in your web browser.
   ```
   git remote add origin <https url to your repository>
   ```
1. Send your code to Github:
   ```
   git add .
   git commit -m "Initial commit"
   git push -u origin main
   ```


### Enable Github Pages

Lastly, enable Github Pages for your project.
To do this, go into the settings of your blog's repository.
Near the bottom of the settings page, you'll see a "Github Pages" section.
Enable your page and select the `gh-pages` branch to use for the site.
After a few minutes, you should see your site up and running!

Now every time you send code to Github from your `main` branch it will be deployed to your site hosted by Github Pages.
If you're not very familiar with Git, [here are some good resources to learn more](https://try.github.io/).
(Perhaps, I'll do a tutorial on Git in the future.)

## Wrapping up

If you've followed along, you've created a blog and it's online now!
Going forward, the [Hexo documentation](https://hexo.io/docs/) will be your friend.
You can also watch the [excellent video tutorials of Mike Dane](https://www.youtube.com/watch?v=Kt7u5kr_P5o&list=PLLAZ4kZ9dFpOMJR6D25ishrSedvsguVSm&ab_channel=MikeDane) for demonstrations of specific features.

I'm thinking about doing another blog post for more advanced topics, including
* Editing existing themes and using submodules so that it works with Github Actions
* Setting up Google Analytics and comments with Disqus
* Settings in the `_config.yml` that I find improve my quality of life
Let me know if there's an appetite for this.

Now that your blog is setup, what are you going to write about?