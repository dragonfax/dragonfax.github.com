---
layout: post
title: "I'm just more comfortable in VI"
date: 2013-04-10 10:54
comments: true
categories: 
---

I've been using Evernote for taking notes for a while now. But I really miss taking notes in VIM.

### History

I'm a heavy VIM user. I use it for coding, through and though. So much so, that use VIM-style editor wrapper plugins IDEs such as Eclipse and IntelliJ. Otherwise I find normal 'editors' clunky and un-usable.

When it comes to coding I'm clearly more productive, and happy in a VI like environment, with command modes, regular expressions, and no need for a mouse or arrow keys. It only made sense that I'd use VIM for taking notes and tracking my work.

But the pull of evernote to managem all that non-coding work was very strong.  The convenience of having notes online, available on every platform, including mobile and web, is just something I couldn't resist.

### My Solution

I've been working on an Evernote Command Line Client in ruby for a little while now.

[Rnote](http://github.com/dragonfax/rnote)

Its not yet ready for prime time, yet. Its missing the final touches. But its far enough along for me to use for my own daily note-taking.

The real driving force behind this project was to allow me to take notes using VIM, but still backed by Evernote.

I can fire up:

`$ rnote edit "note title"`

And rnote will pull down the note, convert it to text, and open it in a copy of VIM.  Then it watches the file and saves it back to Evernote, every time I save the file in my editor.

### Realization

Returning to VIM just feels right.

The interesting thing I found, when returning to VIM after a long absense, was that I'm less afraid of change in VIM. Its not just a matter of simple productvity, in keypress count, and typing speed. But theres apprehension when I'm working in an editor that is burried in several layers of application.

VIM is an environment I can predict. And its only one environment providing the UI. When working in a text area in a browsoer, or in an editor embedded in a desktop app, there are several layers on top of that editor. Each providing their own 'modes' and shortscuts and commands. Each taking priority over the other for different types of input. And each capable of changing the your world in the middle of an editing session.

If I fat finger a typing sequence in some other editor, anything can happen. And the results, I've found, can be unexpected and incomprehensible. I've had experiences where the cursor leaps to a random location in the text, drops a few lines, and starts adding new characters. Other situations have seen my input leap to another document, and start making changes there. And then there is the worse case scenerio of the window just closing altogether, withloss of editor history, and without any sort of save.

In VIM, no matter what happens, I know all I have to do is hit 'u' and magically any bad typing sequence is completely undone. And best of all, if I did type something wrong, I probably know what it was from the effects that occured. Because it has a consice and regular interface that hasn't changed over the years, and isn't different based on the environment.

Of course, I lose WYSIWYG formatting (do we still use that word?), such as bold, italic, and font sizes.  But I don't really miss them.  And I get back indentation, a powerful organization tool. Just ask the python guys.


### Plans

I'm planning to add markdown support, so that I cna have the best of both worlds: pure text editing, but also allow for some formatting. I'm already used to markdown elsewhere in the web, such as octopress and github.


