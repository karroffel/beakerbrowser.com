---
title:    Create a site
category: Get started
order:    2
redirect_from:
 - /docs/howto/publish-a-site.html
---

<small>Prerequisite: [Install Beaker and Bkr](/docs/howto/install.html)</small>

Make sure Beaker is running, then run these commands:

```bash
mkdir ~/mysite
cd ~/mysite
bkr init
```

You will be asked to give a title, description, and author.

```bash
Initializing /Users/paulfrazee/mysite

This utility will walk you through creating a dat.json file.
It only covers the most common items, and tries to guess sensible defaults.

? title: mysite
? description: My new site!
? author: paulfrazee

About to write /Users/paulfrazee/mysite/dat.json

{
  "title": "mysite",
  "description": "My new site!",
  "author": "paulfrazee"
} 

? Is this ok? Yes
```

When it is done, you will receive a URL like this:

```bash
Created new site
dat://ff34725120b2f3c5bd5028e4f61d14a45a22af48a7b12126d5d588becde88a93/
```

This is your site's URL. You can open it in Beaker, and you'll see the manifest you created during init.

### Publish files

In the directory of the site you created, run these commands:

```bash
echo "<h1>Hello, world</h1>" > index.html
bkr publish
```

You'll see similar output to this:

```bash
Running a diff...
dat://344c140462779e2737987c706e16840662a9deafa620996bb6638058b5fa4c07/

1 new file, 0 updates.

    new file:  /Users/paulfrazee/mysite/index.html

Publishing dat://344c14..07
? Publish? (y/N) y
2 files (332 B)
1 added, 0 updated
```

Your site now says "Hello World" when you visit it in Beaker.

Using this flow, you can add many more files, and update the existing files as well.

### How to clone

Beaker stores all Dat sites in an internal database. To work on a site in a new directory, you "clone" it into a folder, then publish updates back into Beaker.

Create the folder you want to clone the site into, then run this command:

```bash
bkr clone <url> # give the url of the target site
```

You will see output similar to this:

```bash
Checking out dat://ff3472..93 into /Users/paulfrazee/mysite
7 files created
```

You can now edit the files and [publish changes](#publish-files).

### How to fork

If you do not own a site, you will see a prompt similar to this when you try to publish changes:

```bash
Running a diff...
dat://316a27810b2886a2b2cb8c9d0e57a0b1b07aa9f47a000c61de47e2f87b6cddfe
Cannot write: not the archive owner
```

To solve this, you must fork the site. "Forking" means to make a new copy at a new URL which you control.

```bash
bkr fork <URL> # give the url of the target site
```

If you're in the directory of a site you want to fork, you don't need to give the URL:

```bash
bkr fork
```

You will see output similar to this:

```bash
Forking dat://fdad0f..80, please be patient...

Checking out into /Users/pfrazee/mysite
2 files created
New url: dat://1322af7a09027ff2b80b250ae410e33873a788000066a9996365095838d02069
```

You can now make changes to the new site.