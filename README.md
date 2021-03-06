# ng-cake-recipes

Synopsis

This is the repo where we attempt to learn, teach, and apply AngularJS with CakePHP.

There will be 2 major sections:

 1. Our notes
 2. Our summary of ng-rails at fullstackio

## Our notes


## Summary of ng-rails

 1. Introduction
   1. Motivation:Combining the most popular web and server frameworks, AngularJS and Rails, this tutorial will show you how to to connect the two,    structuring for code growth, show community conventions for interacting client and server and best practices to run production applications.
     

   2. What we are going to learn: Best practices for integrating AngularJS with Rails
How to communicate between models in the browser and models in your Rails application
How to write your own custom DOM elements using directives
The power of Angular services and when to write your own
How to build a user login and registration system
How to work with external APIs in Angular
How to deal with SEO on an AJAX site.

  3. Finished demo product: We will make API requests to Youtube to get data, load different movies with charts and use Angular router to create different pages.

 2. Setting up: requires Vagrant. For Ubuntu there's a need to run sudo apt-get install nfs-kernel-server.'
   1. Prereqs: Going to be using Ruby and a little node.js
   2. Setting up environment: Visit: https://github.com/fullstackio/ng-rails-vagrant, unzip and fire up vagrant ('vagrant up')
   3. Generate Rails Boilerplate: Go ~/shared, enter: gem install rails --version=4.0.1 && rails new popcorn && cd popcorn
   4. Integrating AngularJS: open up ~/shared/Gemfile, Enter this:'  gem 'angularjs-rails', "=1.2.6" gem 'bootstrap-sass-rails', "=3.0.3.0" And remove turbo links
   5. Go to the VM enter this in ~/shared/popcorn: bundle install, to run the rails server: bundle exec rails server
   6. Installing the views: enter this in VM terminal -> rails generate controller popcorn index, open up config/routes.rb enter: root 'popcorn#index' 
   7. Our first Angular template: Open app/views/layouts/angular.html.erb and give it the contents from URL in the video.
   8. Use our layout: open app/controllers/popcorn_controller.rb and render the angular layout, which will be create later. Code in video.
   9. A little bit more markup: Adding more markup.
   10. Add Twitter Bootstrap CSS: open app/assets/stylesheets/applcation.css and enter *= require twitter/bootstrap
   11. Add angularJS to application.js: Open app/assets/javascripts/application.js And add //=require angular and remove 'turbolinks' and 'JQuery' AND create a new dir, app/assets/javascripts/app, and create a app/assets/javascripts/app/app.js with -> angular.module('popcorn', []);
 3. Our First Controller - MoviesController
   1. Intro: Start writing Angular code. First we need to create the movie posters view. We need HTML view and Angular controller.
   2. Creating our MoviesController: Follow the code given in the video for the function defining syntax.
   3. Basic scopes: Controller takes in two arguments. The name of the controller and a function that defines the controller's behavior.
   4. Dummy Movies: This is basically the lorem Ipsum of the data that we are using to populate the website with.
   5. Basic Movies View: We will learn how to use attribute 'ng-repeat' to set each element to the variable movie. ng-repeat is like an each loop in ruby.
   6. Adding details to Movies View: Add more tags to have a more complete webpage.
   7. Adding CSS: Copy stylesheet from: http://bit.ly/popcorn-css and save it in app/assets/stylesheets/oopcorn.css.scss
   8. Basic Favorites: Add more markup to support favorite function, we learn to use ng-if and ng-click for "if" and "click" functions in the markup.
   9. Introductions to directives: "ng-if" and "ng-click" are called directives. In Angular, directives will be used aplenty. 
   10. Implementing addFavorite/removeFavorite: We define functions add and remove favorite.
  
 4. Setting up Routing
   1. Introduction: Our aim is to create an individual page for each of the movies.
   2. Create a new controller: Set up a `MovieController` in app.js to set up pages for the movies
   3. Setting up the router: Load ngRoute in application.js and includes in this 'ngRoute' inside `MoviesController`. The idea behind this  is similar to routes.php in cake.
   4. Creating the HTML template: We can provide a template view by putting it in `app/public/templates`. Create movies.html.
   5. Creating a new namespace: All the controller code is currently in app.js, by creating a namespace, we modularize the code to a controller folder, one file per controller.
 5. Movie Page & Services
   1. Movie page structure: Add a new route to each individual movie page, create a `MovieController` and a movie template for each movie view.
   2. A Route Detour: when refresh, rails will take over the routing component. This will prompt an error. We will configure in rails to pass the Url to Angular to handle in routes.rb
   3. A service: We learn here to write a service. A service is to provide data to multiple controller without duplicating the code. These are singleton objects.
   4. Back to our service: Move the data movies data into MovieService.js and we need to tell the controllers to take in the service as part of its function argument and not forgetting loading in app.js as well.
   5. Back to the Movie page: Fill out the movie.html template with the provided code. Load the `MovieService` in `MovieController` and use `$routeParams` to get each of the movies from the array. The link to the video still wouldn't work due to a security component in Angular. To get around this we need to load `$sce` library and use it as follow as in the tutorial.
   

