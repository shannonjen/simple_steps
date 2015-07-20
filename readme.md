#Simple Steps to Create a Sinatra/ActiveRecord/Rake Web App
##Three steps to create database
1. Create Gemfile to import necessary gems and run bundle install
-gem 'activerecord'
-gem 'sinatra-activerecord'
-gem 'sqlite3'
-gem 'rake'
2. Require gems and set your database in your main app (ex: app.rb)
-require 'sinatra'
-require 'sinatra/activerecord'
-set :database,"sqlite3:<database>.sqlite3"
3. Create Rakefile
-require './app'
-require 'sinatra/activerecord/rake'
##Next three steps to create a table
1.Create migration using rake on command line. This will create a db directory containing a migrate subdirectory with a timestamped_create_users_table.rb file
-$rake db:create_migration NAME=create_users_table
2. Add a create_table method to the change method in the CreateUsersTable class within the timestamped_create_users_table.rb file. Ex:

class CreateUsersTable < ActiveRecord::Migration

  def change

  	create_table :users do |t|

  		t.string :username

  		t.string :password

  		t.string :fname

  		t.string :lname

  	end

  end

end
3. Run the database migration usining rake on commandline
-rake db:migrate
##Create a models.rb file within your main directory to represent your tables

Each table will have a class. 

Ex. for User:
-class User < ActiveRecord::Base
-end

At end of main ruby app file, require in your models:

-require './models'







