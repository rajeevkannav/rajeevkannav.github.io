---
title: "Install Rails 7 Edge Alpha "
date: 2021-03-19T21:40:30+05:30
categories:
 - rails7
 - edge-rails
---

### Setup your app directory

    mkdir rails7-edge-alpha-app
    cd rails7-edge-alpha-app
  
### Specify your Ruby version
    touch .ruby-version
    echo 'ruby-3.0.0' > .ruby-version

### Setup Gemfile with edge rails7
    touch Gemfile
    printf "source 'https://rubygems.org'\nruby '3.0.0'\n\n\ngem 'rails', github: 'rails/rails'" >> Gemfile
    bundle install

### edge Rails7
  
    bundle exec rails new . --dev --force
  
  ```The --dev will tell rails to use the latest development version you just installed. Otherwise Bundler will try and find gem version on RubyGems.org that are not available yet.```
  
### ta-daa!!!

    bundle exec rails s
