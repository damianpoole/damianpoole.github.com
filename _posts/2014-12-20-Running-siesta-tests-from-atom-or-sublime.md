---
layout: post
title: Running Siesta tests from Atom or Sublime
---

This post is not about how to use Siesta for unit testing, more a quick guide on how to
get setup using PhatomJS to run your tests from Atom or Sublime.

The main benefit to using this over the standard web ui is speed. From a keyboard shortcut you can have your test pass or fail within a second.

### Atom

My current IDE of choice so i'll go over the setup for this one first.

Firstly [install this package](https://github.com/noseglid/atom-build) which allows you to build your current project directly from atom.

Once you have done that all you no need to do is create a .atom-build.json file which tells the package how to build your project.

Example .atom-build.json file.

    {
        "cmd": "PATH_TO_SIESTA/bin/phantomjs",
        "args": [ "LOCALHOST/test.html", "--filter {FILE_ACTIVE_NAME}"],
        "sh": true
    }

By using --filter we are telling PhantomJS to only run the test we are looking at within our IDE.

### Sublime

Luckily Sublime supports build systems out of the box so no packages are needed to be installed.

To create a new build system go tools > build systems > new build system.

Example siesta.sublime-build.

    {
        "cmd" : ["PATH_TO_SIESTA/bin/phantomjs LOCALHOST/test.html --filter $file_name"],
        "shell": true
    }

No you just need to ensure you are using this build system for your project and you can now run a single test just like in Atom.
