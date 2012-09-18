# class 2

## review:

* clear the screen `ctrl+l`

### generate a new rails project

* `rails new hello` a new rails project called "hello"
* `cd hello/`
* modify Gemfile and add the lines `gem 'execjs'` and `gem 'therubyracer'` then run `bundle install`
* `rails generate controller hello index`
* `rails server`

### use git and github for your version control

* `git init` start a new git repository in the current directory
* `git add .` add all new and changed files to the staging area
* `git commit -m "Initial commit"` commit the files in the staging area
* `git remote add origin git@github.com:[your username]/hello.git` add a new remote repository, called origin
* `git push -u origin master` clone your repository to the remote called origin

### use keys to connect to github

* `ssh-keygen` generate ssh keys
* `less ~/.ssh/id_rsa.pub` view your newly generated ssh key
* copy the key contents to your github account
* For those who created their ssh key, but were still prompted for a password, see [this article](https://help.github.com/articles/why-is-git-always-asking-for-my-password) (you need to change the location that your "origin" remote points to).

### clear any modifications to files since the last commit

* `git checkout .`

## completely remove all new files since the last commit

* `git clean --help` get help on the git clean command
* `git clean -dn` clear all new files and directories, but don't actually do it, just say what will happen
* `git clean -df` clear all new files and directories, for reals

## topics:

* [agile](http://agilemanifesto.org/) programming
* database [migrations](http://guides.rubyonrails.org/migrations.html) and [associations](http://guides.rubyonrails.org/association_basics.html)
* [behavior driven development](http://behaviour-driven.org/) with [rspec](http://rubydoc.info/gems/rspec-rails/frames)
* [representation state transfer](http://guides.rubyonrails.org/getting_started.html#rest)
* [basic security](http://guides.rubyonrails.org/security.html)

## coding:

* rails scaffolding

* `rails generate scaffold tool name:string material:string weight:integer bought_on:date` generate model, views, controllers, and db migration for the "tool" model with specific attributes
* `rake db:migrate` run the database migration to add the "tools" table to your database
* visit [localhost:3000/tools](http://localhost:3000/tools) to see the result

## project 1a: inventory tracking (resource, location)

track resources such as computers, printers, scanners, furniture, office equipment

### resources (suggested attributes)

* resource_type:string
* make:string
* model:string
* purchesed_at:datetime
* serial_number:string
* user_name:string
* salvage_value:float
* location_id:integer

### locaton (suggested attributes)

* address:text
* name:stingnew
* number:string
* jack:string
* floor:string
* room:string

## project 1b: email signup form (person, topics)