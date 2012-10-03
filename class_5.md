# class 5

## routing

Take a look at the [rails guide on routing](http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions)

see your routes `rake routes`

the first column has named routes like "tickets" or "new tickets". you can use these named routes by adding a "_path" to the end.

`tickets_path`

using the `link_to` method

`link_to 'All tickets', tickets_path`

or if you have a ticket object in a variable, say `@ticket`

`link_to "Edit ticket: #{@ticket.title}", ticket_path(@ticket)`

### Standard RESTful routing, with the "ticket" model

Show all tickets

    GET /tickets => tickets#index

Show a ticket

    GET /tickets/1 => tickets#show

New ticket

    GET /tickets/new => tickets#new
    POST /tickets    => tickete#create

Edit ticket

    GET /tickets/12/edit => tickets#edit
    PUT /tickets/12      => tickets#update

Delete ticket

    DELETE /tickets/12   => tickets#destroy

## project 2

* ticketing system (issue, person, tags)

### 0. create a github repository

* name it "tickets"
* clone the blank repository

In your terminal:

    cd rails
    git clone git@github.com:[username]/tickets.git

### 1. create a new rails app

In your terminal:

    rails new tickets
    cd tickets

add to your Gemfile:

    gem 'therubyracer'
    gem 'execjs'

and run `bundle install`

### 2. create a welcome controller with the index action

In your terminal:

    rm public/index.html
    rails generate controller welcome index

### 3. point "/" to the welcome controller and have a look

* config/routes.rb (uncomment line 53 `root :to => 'welcome#index'`)
* in a new terminal `cd rails/tickets`, `rails server`
* browse to http://localhost:3000

### 4. edit the home page

in app/views/welcome/index.html.erb

### 5. create two models and a join table

In your terminal:

    rails generate scaffold ticket title:string description:string status:string
    rails generate model person name:string role:string
    rails generate migration create_people_tickets_join_table

and add the following to the join table migration (in db/migrate)

    def change
      create_table :people_tickets do |t|
        t.integer :person_id
        t.integer :ticket_id
      end
    end

In your terminal, run the migrations

    `rake db:migrate`

### 6. create associations

in app/models/ticket.rb `has_and_belongs_to_many :people`
in app/models/person.rb `has_and_belongs_to_many :tickets`

### 7. save your work

In your terminal:

    git add .
    git commit -m "created basic models and associations"
    git push