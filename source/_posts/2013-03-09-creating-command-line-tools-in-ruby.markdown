---
layout: post
title: "Creating Command Line Tools in Ruby"
date: 2013-03-09 19:48
comments: true
categories: 
---

A Beginners Guide
-----------------

I use RubyMine without doing any rails and doing just what you ask. I write a lot of simple scripts, and large applications, both often usable from a command line.

I still organize my code into a 'project directory'. And point RM at that directory. Instead of just working entirely in a file, and trying to point RM at the file alone. This seems to be what IDE's prefer. This lets RM create its `.idea` directory to hold all of its project related settings.

This may mean that some projects consist of nothing more than a directory (for the project) and a single file in that directory (the single script which is really the only content in that project).

Benefits of a Project Directory
-------------------------------

You'll soon find you add more files to any project anyways. Both additional coding and various utilities which are part of the great benefit of ruby.

* gem
* rake
* tests

The `project directory` pattern, also lets you version the code with popular VCS such as git, and even upload to social coding sites like github.


Project Setup
-------------

I don't bother with any sort of "project type". In fact I don't create projects from with RubyMine at all. I just create a directory, and then open that directory with RM (whether from the File Menu, or via the "mine" command line tool that RM installs).


`project/`

Of course `project` isn't the real name of the project, or the directory I create, I'm just using it as a generic name here. I would actually name the directory (and project) after the scripts or subject matter of the work they do.

NOTE: *currently there is a bug in the `mine` command in RM 5 where it won't open a second project window.*

Obviously if this is a project that includes any command line scripts I'll put those in a `bin` directory, just for organization purposes. I don't like to clutter the root project directory with all sorts of things. There are too many tools that _require_ their settings files in the project root, so the fewer the better.

`project/bin/`

Like I said, various other utilities prefer their settings files in the project root, so you may find yourself using some of them.

    project/Gemfile
    project/Rakefile
    project/project.gemspec
    project/README.md
    project/.rdoc_options
    ...

As soon as I have some automated testing for the scripts (which I admit isn't immediate) I put all test code under a `test` directory, but I further categorize those according to the scope of the tests or how often I would run them during development. And I'll go so far as to add quck Rake tasks that are just aliases for the commands necessary to run the tests. So I dont' have to remember which test runner, or type the full paths each time.

    project/test/
    project/test/unit/
    project/test/unit/some_component_test.rb
    project/test/integration/

Finally, as the project grows, and I add more scripts or want to reuse some of the code within external projects, I'll add a `lib` directory, and use some standard practices for how to organize that.

    project/lib/
    project/lib/project.rb

And as the project continues to grow and get more complicated, more organization of the content is required, after a little refactoring. Note the `cmd` directory to contain the actual top-level code of various workflows a particular script can go through.

    project/lib/project/
    project/lib/project/other_stuff.rb
    project/lib/project/cmd/
    project/lib/project/cmd/one_command.rb
    project/lib/project/cmd/another_command.rb

Of course the original `project.rb` 'requires' all of these lib files. Ruby loads pretty fast, so I don't bother too much with managing dependencies between the ruby files within the same project. Its really all about code readability.


Better Command Line Apps
------------------------

There is nothing wrong with starting with a single script file and writing minimal boiler plate coding. And thats probably the best way to start.

    #!/usr/bin/env ruby
    
    =begin
    
    this is a script blah which does whatever
    
    EXAMPLE
    
    $ script <options> <arguments
    
    =end

    def main(args)
      whatever
    end

    main(ARGV)
    exit(0)


But writing even better command line apps in ruby is pretty easy. There are popular gems which handle a lot of the infrastructure for you.

You can start with something as simple as [OptionParser](http://ruby-doc.org/stdlib-1.9.3/libdoc/optparse/rdoc/OptionParser.html)

Then as you build more code in your scripts you can graduate to a bit more infrastructure with a gem like [Methadone](https://github.com/davetron5000/methadone)

Finally, when you're writing full blown command line applications, with many "internal" commands like "git submodule init <repo", you can ascend to something much more heavy-weight like [GLI](https://github.com/davetron5000/gli)


Testing Command Line Apps
-------------------------

Unit testing is the pretty much the same, no matter what type of application your writing. You're not using real services or combining components, but just isolating the internal components and using them in a purely internal manner. So not much changes there for command line tools.

But when it comes to integration or full command-line testing of my scripts, I'm actually a big fan of `cucumber/aruba`. I'm not big on TDD, I'm a bit too pragmatic for that. But for command line tools, the series of use cases is already laid out pretty plainly in the set of options available. Even for interactive commands this makes a series of `feature` files conveniently double as documentation for the tool.


    Feature:
      Create and manipulate notes in Evernote.
    
      Background:
        Given I am logged in as me
        And I have 0 notes
        
      Scenario: Show note
        Given that I have 1 note named "foo" with content "bar"
        When I run `rnote show note --title "foo"`
        Then the output should contain "bar"
        
      Scenario: Show note, from multiple notes
        Given that I have 2 notes named "foo"
        When I run `rnote show note --title "foo"` interactively
        And I type "1"
        Then the output should contain "foo"



Installation
------------

As for installation and packaging for your scripts, so that they can be shared and reused by the rest of the world, look no further than the same 'gem' utility that you've already been using all along in ruby for depenencies. 

The `gemspec` you create when writing a new gem to share, can be told about your scripts and other command line utilities. It will then wrap them up with the rest of your code, install them in a good location, and even fix up the PATH so the user can find them when the time comes.

In fact this works so well, your gem can be composed of nothing but these `bin` scripts. With no other re-usable code included. 

[cat-dog](https://github.com/dragonfax/cat-dog) is a harmless little gem I whipped up as an example for something else. It contains no lib directory at all and no other ruby other than a single command line script.

Ruby Without Rails
------------------

I've run into a lot of Rails developers who aren't cognisant of what _is_ Rails and what _is_ ruby. i.e. what you're left with when you remove the Rails. Obviously the server and templating, databasing, MVC are all gone, as are a portion of convenience methods added to every-day objects. 

The goods new is that you're still left with quite a lot. And if you find you miss something, its easy to add it back in with by including a gem or two. For instance, if you enjoy using an ORM like active-record it can be included back into your application, without rails, with little fuss. 

    require 'activerecord'


Full Featured RubyMine
----------------------

Finally, using RubyMine features more heavily during development. Everything available when working with rails is available for command line applications.

You can run your commands from RM and use its debugger just the same as rails.
Just like any IDE you can set up "run" profiles with the arguments you want to test the script on, and run or debug the script through the IDE. Personally, I never use a command-line debugger. If I need to fire up a debugger to troubleshoot some issue, then I'll launch the program in an IDE. The benefits of an IDE debugger with "heads-up" display of all the pertinent details, and visually following the script through execution, is just irreplaceable.








