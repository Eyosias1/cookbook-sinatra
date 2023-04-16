# Sinatra 101

This repository is a tutorial for a first contact with the Sinatra gem, a DSL for quickly creating web applications in Ruby with minimal effort.

## Setup

1. Create a new folder to put your Sinatra app in: `mkdir ~/code/$GITHUB_USERNAME/cookbook-sinatra` and `cd ~/code/$GITHUB_USERNAME/cookbook-sinatra`
2. Create a `Gemfile` to specify which gems you'd like to use in this project: `touch Gemfile`
3. Add the following code to your `Gemfile`:
    ```
    source "https://rubygems.org"

    gem "better_errors"
    gem "binding_of_caller"
    gem "pry-byebug"
    gem "sinatra"
    gem "sinatra-contrib"
    gem "thin"
    ```
4. Run `bundle install` to fetch the gems specified in the `Gemfile`
5. Create a new git repository with `git init`
6. Add and commit the two files to the git repository with `git add .` and `git commit -m "Init sinatra project"`
7. Create a new repository on GitHub and link the local repository to the remote one with `gh repo create --public --source=. && git push origin master`

## Sinatra app

1. Create a new file named `app.rb` at the directory root which will be the Sinatra app main file, the entry point, the one we want to run
2. Copy-paste this boilerplate to your `app.rb` file:

    ```
    require "sinatra"
    require "sinatra/reloader" if development?
    require "pry-byebug"
    require "better_errors"

    configure :development do
      use BetterErrors::Middleware
      BetterErrors.application_root = File.expand_path(__dir__)
    end

    get "/" do
      "Hello world!"
    end
    ```

3. Run `ruby app.rb` and open your browser at `localhost:4567`
4. To create a new view, create a new file in the `views` folder, and use `erb :view_name` in the controller to render the view
5. To create a new route, use `get "/path" do ... end` or `post "/path" do ... end` to handle HTTP requests
6. To handle parameters in the URL, use the `params` hash
7. To share data between the controller and the view, use instance variables
8. To create a layout, use a file named `layout.erb` in the `views` folder, and use `<%= yield %>` to render the view
9. To make your app visible to others, use `set :bind, "0.0.0.0"` to allow external incoming requests
10. To share your app with people outside the local network, use `ngrok`
