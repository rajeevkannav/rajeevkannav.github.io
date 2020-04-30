---
layout: post
title: Dockerization a rails application with docker-compose    
excerpt: "docker-compose  for rails (development environment)"
modified: 2016-12-02
tags: [Docker, Rails, Docker-Compose]
comments: true
---

### [Docker-compose](https://docs.docker.com/compose/)

Compose is a tool for defining and running multi-container Docker applications.
  
### use Docker Compose to set up and run a Rails app
 
##### Define the project 
 Create a `Dockerfile` for Rails app
 
    FROM ruby:2.3.3
    RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
    RUN mkdir /myapp
    WORKDIR /myapp
    ADD Gemfile /myapp/Gemfile
    ADD Gemfile.lock /myapp/Gemfile.lock
    RUN bundle install
    ADD . /myapp

 Create a `Gemfile`
 
    source 'https://rubygems.org'
    gem 'rails', '5.0.0.1'
    
 Create a `Gemfile.lock`
 
    touch Gemfile.lock
    
 Create `docker-compose.yml` 
    
    version: '2'
    services:
      db:
        image: mysql
      web:
        build: .
        command: bundle exec rails s -p 3000 -b '0.0.0.0'
        volumes:
          - .:/myapp
        ports:
          - "3000:3000"
        depends_on:
          - db
  
    
##### Build the project

    docker-compose build
    
  Connect the database
  Replace the contents of `config/database.yml` with the following:
  
    development: &default
      adapter: mysql2
      encoding: unicode
      database: myapp_development
      pool: 5
      username: mysql_user_name
      password: mysql_password
      host: db
    
    test:
      <<: *default
      database: myapp_test
    
    
##### Boot Application

    docker-compose up
    
  if you're done everthing correctly, You must have seen something like following on terminal
  
    myapp_web_1 | [2014-01-17 17:16:29] INFO  WEBrick 1.3.1
    myapp_web_1 | [2014-01-17 17:16:29] INFO  ruby 2.2.0 (2014-12-25) [x86_64-linux-gnu]
    myapp_web_1 | [2014-01-17 17:16:29] INFO  WEBrick::HTTPServer#start: pid=1 port=3000

##### Setup DataBase
    
    docker-compose run web rake db:create


##### Get Set go
    
   VISIT [http://localhost:3000/](http://localhost:3000/)
   
##### General Error(s)
   
    A server is already running. Check /myapp/tmp/pids/server.pid. 
    delete the file tmp/pids/server.pid to fix this
    
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
