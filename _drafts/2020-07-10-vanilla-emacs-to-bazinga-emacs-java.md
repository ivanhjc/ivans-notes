---
title: Vanilla Emacs to Bazinga Emacs: Java
excerpt: "The complete guide to turn vanilla Emacs to a Java IDE"
last_modified_at: 2020-11-02
categories:
  - productivity
tags:
  - emacs
  - java
---

Emacs is an old, open-source, not-so-normal plain text editor that boasts the power of being used to do almost anything with the same operational acquaintance that can be fully tailored for you. Using Emacs feels like a wizard in zen mode wielding his magical stick to construct whatever comes into his mind. It's a programmer's best friend but I also suggest everyone learns and uses it as soon as possible!

Java is a programming language and platform widely used to develop high-concurrent server-side applications by a majority of companies such as Google, Alibaba, Amazon, etc. It has been showing high job demands on the market and has a large base of developers. Currently the most popular tools for developing in Java are Intellij IDEA, Eclipse, and NetBeans. Using Emacs for writing Java programs isn't a fashion yet, mostly because of the lack of supports from both commercial companies and the open-source community, which is the ramification of many other causes such as a greater learning curve of Emacs and Lisp, but it's definitely feasible to customize Emacs into a full-fledged production-ready IDE.

The core of this idea is LSP - the Language Server Protocol, which is a set of APIs defined by Microsoft to assist code writing with features common in modern IDEs such as real-time diagnostics (also called linting), auto-completion, code navigation, syntax highlighting, code formatting, debugging, refactoring etc. Without these features coding would be hard and unproductive. LSP has been integrated into MS Code, the new fashion of coding. Besides, features such as project awareness, version control, framework support also play an important role for boosting your productivity. In vanilla Emacs (i.e. the one without any user configuration) all these features are not pre-packaged but scattered all around the Internet as packages and code snippets contributed by open-source advocators and enthusiasts so all we need to do is to piece them together. This is not an easy task but a good yet destined way to learn and become a true Emacs wizard.

If you're new to Emacs you can type =C-h C-a= (short for "Press Ctrl and H together, release, and then press Ctrl and A together") to open the welcome screen (which should be displayed already if you have just downloaded it and opened it for the first time), where you can find useful information to start with Emacs, such as [[elisp:(help-with-tutorial)][Emacs Tutorial]] (or type =C-h t= to enter the tutorial directly). The cool thing about Emacs is that you can always "ask" it when you have a problem about it and find the answer (almost) right inside of it, because it's very well self-documented - every command, variable, and key stroke is documented and easy to look up (using =C-h f=, =C-h v=, =C-h k= respectively), and there are extensive manuals and tutorials about Emacs and Lisp and many other topics in the Info reader (started with =C-h i=), where you can easily navigate through the pages and indexes, and you can add your own manuals. Being able to work offline is a bliss if you are in a region where Internet access is problematic, and the Internet itself is of cource powerful and useful, but has limitations such as its mercurial nature. In this way we can keep our work in a constant zen mode and save the time and trouble of being distracted while scrolling through the Internet webpages. When you get a bit familiar with the basics you can check the [[file:emacs-commands-quick-reference.org::*Commands][Emacs commands quick reference]] for a number of most commonly used commands.

