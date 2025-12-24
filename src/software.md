# Software and Setup

You will need the following software when going through this book. This is to ensure you can run examples and receive feedback on your solutions from the code you have constructed.

* NodeJS, <https://nodejs.org/en/download>
* Git, <https://git-scm.com/>
* Text Editor
  * VSCodium- <https://vscodium.com/>
  * Kate Editor - <https://kate-editor.org/> 
  * Helix - <https://helix-editor.com/>
  * Vim - <https://www.vim.org/download.php>
  * CudaText - <https://cudatext.github.io/>
  * Lite-XL - <https://lite-xl.com/>
* Access to a unix-shell (or if you really want to, powershell is somewhat viable).

> **Why don't you recommend Visual Studio Code?**. Simply put, **Microsoft** has built in a lot of undesirable features into their text editor. It has become incredibly disruptive to productivity and for learners. What was once a reasonably good product is better captured by `VSCodium`.

## What is NodeJS?

NodeJS is a **Virtual Machine** that allows you to execute javascript locally on your machine without a web-browser.

It has been used to build a variety of applications from large and complex web applications to small services running on a raspberry-pi.


## What is Git?

Git is a source-code management system for projects. It is used heavily in the software industry as part of collaboration but also it can be used quite easily for any project that involves text.

Git is a distributed system as well, when you create a repository, you will create a local repository on your own device. Afterwards, you can then create repository on another device or service (like Github or Codeberg) and synchronise your code on your system with the one over there. You are also not locked in to using just 1 service, you can use any number.



## What is a Text Editor?

A text editor is a program that allows you to write text to a document. Similar to `Word` but its focus is usually on code or markup documents like HTML or Markdown.

There are a large number of text editor and this really comes down to preference and productivity.

It is okay to switch to another text editor later, it won't majorly effecet your understanding of a programming language by you may need to get familiar with a new set of shortcuts and UIs.

## How do these all connect? 📒

Each piece of software serves a particular role, however it can be difficult to see how it all fits together. Let's show their relation to each other.

* Text Editor
  * You will write code using this tool
  * You save .js files
  * It will show some basic syntax in your code (but not logic errors)

* NodeJS
  * It can execute javascript code
  * Used to run desktop and server side application
  * Is used with a package manage called `npm` to use existing libraries

* Git
  * Resources for this course (including code snippets and documentation) are available via git
  * The standard version control software, used maintain change sets of source code and collaborate with other developers using services like Github, GitLab, Codeberg and Forgejo

When starting out, you mostly focus on using a text editor and nodejs.
