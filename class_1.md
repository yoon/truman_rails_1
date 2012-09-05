# class 1

## topics:
* hello, expectations, contact info
* our development environment: [ubuntu 12.0.4LTS](https://wiki.ubuntu.com/Releases), on usb, [sublime text](http://www.sublimetext.com/)
* version control with [git](http://git-scm.com/book/en/Getting-Started-About-Version-Control) and [github](https://github.com/features/projects)
* what is [ruby](http://www.ruby-lang.org/en/about/)? what is [rails](http://guides.rubyonrails.org/getting_started.html#what-is-rails)?
* mvc - [model view controller](http://guides.rubyonrails.org/getting_started.html#the-mvc-architecture)
* what are we doing? [web applications](http://thepaisano.files.wordpress.com/2008/04/rails2.png)
* terms ruby, [rvm](https://rvm.io/), rails, [gems](http://rubygems.org/), [bundler](http://gembundler.com/)

### the command line

* [commands](https://help.ubuntu.com/community/UsingTheTerminal#Commands)
* `pwd` print working directory
* `cd` change directory
* `ls` and `ls -la` list contents of directory
* `touch` create a blank file, or change the modified date of an existing file
* `cp` copy a file
* `mv` move
* `mkdir` make a directory
* `rm` remove a file
* `rm -r` remove a directory

### the rails command

* rails [command](http://guides.rubyonrails.org/command_line.html): rails new, rails server, rails generate
* `rails new hello`
* `rails server`
* `rails generate controller welcome index`

### git commands

* `git init` start a new git repository
* `git add .` add all files in the current direct
* `git remote add origin [location]` link to a remote repository called origin at some location
* `git push -u origin master` push the master branch to the remote repository called origin

## coding:

* [try ruby](http://tryruby.org)
* [try git](http://try.github.com)
* [sign up for github](https://github.com/signup/free)

### Dynamic "hello world"

`One plus one is: <%= 1+1 %>`
`The time is now <%= Time.now.strftime("%H%M%S") %>`
`You are runinng rails version: <%= Rails.version %>`

## resources:

* [rails api](http://api.rubyonrails.org/)
* [ruby 1.9.3 api](http://www.ruby-doc.org/core-1.9.3/)
* [rails guides](http://guides.rubyonrails.org/)
* [why’s poignant guide to ruby](http://mislav.uniqpath.com/poignant-guide/)

## books and conferences:

* [agile wed development with rails](http://pragprog.com/book/rails4/agile-web-development-with-rails)
* [the pickaxe book](http://pragprog.com/book/ruby/programming-ruby)
* [version control with git](http://shop.oreilly.com/product/9780596520137.do)
* [railsconf](http://www.railsconf.com/2013) april 29 - may2, 2013
* [windy city rails](http://windycityrails.org/) september 6 - 7, 2012

## setting up rails on ubuntu linux:

* [railsready](https://github.com/joshfng/railsready)
* [smashing magazine's ubuntu setup](http://coding.smashingmagazine.com/2011/06/21/set-up-an-ubuntu-local-development-machine-for-ruby-on-rails/)
