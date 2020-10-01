# Learn Enough Rails

```ruby
gem install rails -v 6.0.3.3
brew install yarn
```



#### Create New Rails App

```ruby
rails _6.0.3.3_ new hello_app
```

- This creates the standard directory and file structure.

#### Bundler

After creating a new Rails application, the next step is to use Bundler to install and include the gems needed by the app.

Bundler is run automatically (via `bundle install` ) by the `rails` command when you did `rails _6.0.3.3_ new hello_app`

But we're going to make some changes to the default application gems and run Bundler again.

*tutorial updates gems such that they are specific versions so you are consistent with the tutorial*

```ruby
cd hello_app
bundle install
```

#### `rails server`

- Before running `rails server` its necessary on some systems to allow connections to the local web server. To enable this, you should navigate to the file `config/enviornments/development.rb` and past in these two extra lines:

  ```ruby
  # Allow connections to local server.
    config.hosts.clear
  ```

- From running `rails new` and `bundle install` we have an application we can run because Rails comes with a command-line script that runs a local webserver.

```ruby
rails server
```



#### Model View Controller (MVC)

- Enforces a separation between the data in the application (such as user information) and the code used to display it, which is a common way of structring a graphical user interface (GUI).
- When interacting with a Rails application, a browser sends a request which is received by a webserver and passed on to a Rails controller, which is in charge of what to do next. In some cases, the controller will immediately render a view, which is a template that gets converted to HTML and sent back to the browser. More commonly for dynamic sites, the controller interacts with a model, which is a Ruby object that represents an element of the site (such as a user) and is in charge of communicating with the database. After invoking the model, the controller then renders the view and returns the complete web page to the browser as HTML.

![mvc_schematic](https://softcover.s3.amazonaws.com/636/ruby_on_rails_tutorial_6th_edition/images/figures/mvc_schematic.png)

#### Hello, World!

- `app/controllers/application_controller.rb`

```ruby
def hello
  render html: "hello, world!"
end
```

- Above, we defined the `hello` method which uses the `return` function to return the HTML text "hello, world!"
- Having defined an action that returns the desired string, we need to tell Rails to use that action instead of the default page. To do this we'll edit the Rails router, which sits in front of the controller and determines where to send requests that come in from the browser.
- In particular, we want to change the default page, the root route, which determines the page that is served on the root URL.
- `config/routes.rb` includes a comment directing us to the [Rails Guide on Routing](https://guides.rubyonrails.org/routing.html), which includes instructions on how to define the root route. The syntax is:

```ruby
root 'controller_name#action_name'
```

- In the present case, the controller name is `application` and the action name is `hello`.

#### Version Control with Git

- One time setup steps:

```git
Listing 1.12: Configuring the name and email fields for Git.
$ git config --global user.name "Your Name"
$ git config --global user.email your.email@example.com
```

- Optional but convenient step and set up an alias, or synonym for the commonly used `checkout` command

```git
$ git config --global alias.co checkout
```

In the tutorial, Michael Hartl uses the  `git checkout` , but in practice he almost always uses `git co` for short.

- Initialize a new repository:

```git
git init
git add -A
git status
git commit -m "Initialize repository"
git log
```

- If you accidentally delete a file, you can undo changes by running:

```git
git checkout -f
git status
```

- You can create copies of a repository where you can make changes without modifying the parent files. This copy is called a branch. In most cases the parent repository is the master branch, and we can create a new topic branch by:

```git
git checkout -b modify-README
# Switched to a new branch and named it 'modify-README'
git branch
# master
# *modify-README
```

