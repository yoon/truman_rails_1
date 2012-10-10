# class 6


## project 2:

### 12. add a link for creating tickets

View: app/views/welcome/index.html.erb

    <h2>Create a new ticket</h2>
    <%= link_to "Create a ticket", new_ticket_path %>

### 13. add a listing of assigned tickets

View: app/views/welcome/index.html.erb

    <h2>Assigned tickets</h2>

    <%- @people_with_tickets.each do |person| %>
      <%= person.name %>'s tickets
      <ul>
        <%- person.tickets.each do |ticket| %>
          <li>
            <%= link_to ticket.title, ticket_path(ticket) %>
          </li>
        <%- end %>
      </ul>
    <%- end %>


Controller: app/controllers/welcome_controller.rb

    @people_with_tickets = Person.people_with_tickets

Model: app/models/person.rb

    def self.people_with_tickets
      self.joins(:tickets).all
    end


### 14. redirect old list of tickets

Controller: app/controllers/tickets_controller.rb

    redirect_to root_path

### 15. add a "remove" button

View: app/views/tickets/edit.html.erb

    <br/>
    <br/>
    <p><%= button_to 'Remove this ticket', @ticket, method: :delete, data: { confirm: 'Are you sure?' } %></p>

### 16. add person management

In your terminal:

    rails generate controller people

Routes: config/routes.rb

    resources :people

Controller: app/controllers/welcome_controller.rb

    @people = Person.all

View: app/views/welcome/index.html.erb

    <h2>Manage people <%= link_to "+", new_person_path %></h2>
    <ul>
      <%- @people.each do |person| %>
        <li><%= link_to person.name, edit_person_path(person) %></li>
      <%- end %>
    </ul>

View: app/views/people/edit.html.erb

    <h1><%= @person.new_record? ? "New" : "Editing"%> person</h1>
    <%= render 'form' %>
    <%= link_to 'Back', people_path %>
    <%- if !@person.new_record? %>
      <br/>
      <br/>
      <p><%= button_to 'Remove this person', @person, method: :delete, data: { confirm: 'Are you sure?' } %></p>
    <%- end %>

View: app/views/people/_form.html.erb

    <%= form_for(@person) do |f| %>
      <% if @person.errors.any? %>
        <div id="error_explanation">
          <h2><%= pluralize(@person.errors.count, "error") %> prohibited this person from being saved:</h2>
          <ul>
          <% @person.errors.full_messages.each do |msg| %>
            <li><%= msg %></li>
          <% end %>
          </ul>
        </div>
      <% end %>
      <div class="field">
        <%= f.label :name %><br />
        <%= f.text_field :name %>
      </div>
      <div class="field">
        <%= f.label :role %><br />
        <%= f.select :role, Person.roles %>
      </div>
      <div class="actions">
        <%= f.submit %>
      </div>
    <% end %>

Model: app/models/person.rb

    def self.roles
      ["user", "admin"]
    end

Controller: app/controllers/people_controller.rb

    class PeopleController < ApplicationController
      def index
        redirect_to root_path
      end
      def show
        redirect_to people_path
      end
      def new
        @person = Person.new
        render :action => "edit"
      end
      def edit
        @person = Person.find(params[:id])
      end
      def create
        @person = Person.new(params[:person])
        if @person.save
          redirect_to root_path, notice: 'Person was successfully created.'
        else
          render action: "new"
        end
      end
      def update
        @person = Person.find(params[:id])
        if @person.update_attributes(params[:person])
          redirect_to root_path, notice: 'Person was successfully updated.'
        else
          render action: "edit"
        end
      end
      def destroy
        @person = Person.find(params[:id])
        @person.destroy
        redirect_to root_path, notice: 'Person was successfully removed.'
      end
    end

### 17. put the application's title on every page

in app/helpers/application_helper.rb

    def flash_messages
      messages = [:error, :notice, :warning].map do |key|
        if flash.keys.include? key
          content_tag :p, :id => key.to_s do
            "#{key}: #{flash[key]}"
          end
        end
      end
      messages.join.html_safe
    end

in app/views/layouts/application.html.erb

    <h1>Truman ticketing system</h1>
    <%=flash_messages %>
    <%= yield %>
