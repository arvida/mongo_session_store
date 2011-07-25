# MongoSessionStore

## Description

This is a fork of the DataMapper session store, modified to work with MongoMapper and Mongoid.  Also included is a generic MongoStore that will work with any (or no!) Mongo ODM.

## Installation

The current version is only compatible with Rails 3

    gem install mongo_session_store

However if you want to use it with Rails 2.3.x, you just have to install the latest 1.x version

    gem install mongo_session_store --version=1.1.2

## Usage with MongoMapper

In your Gemfile:

    gem "mongo_mapper-rails3", :require => "mongo_mapper"
    gem "mongo_session_store"

In the session_store initializer (config/initializers/session_store.rb):

    ActionController::Base.session_store = :mongo_mapper_store

## Usage with Mongoid

In your Gemfile:

    gem "mongoid"
    gem "mongo_session_store"

In the session_store initializer (config/initializers/session_store.rb):

    Rails.application.config.session_store :mongoid_store

## Usage with any other (or no!) ODM

In your Gemfile:

    gem "mongo" # or an ODM that requires mongo
    gem "mongo_session_store"

In the session_store initializer (config/initializers/session_store.rb):

    Rails.application.config.session_store :mongo_store
    # if you're not using MongoMapper or Mongoid, you also need to set a database, e.g.:
    ActionDispatch::Session:MongoStore::Session.database = Mongo::Connection.new.db('my_app_development')

## Development

To run all the tests:

    rake

To switch to the Rails 3.0 Gemfile.lock:

    rake use_rails_30

To switch to the Rails 3.1 Gemfile.lock:

    rake use_rails_31

To run the tests for a specific store:

    MONGO_SESSION_STORE_ORM=mongo_mapper bundle exec rspec spec
    MONGO_SESSION_STORE_ORM=mongoid bundle exec rspec spec    

## Contributors

* Nicolas Mérouze
* Chris Brickley
* Tony Pitale
* Nicola Racco
* Matt Powell
* Ryan Fitzgerald
* Brian Hempel

## License

Copyright (c) 2010 Nicolas Mérouze
Copyright (c) 2009 Chris Brickley
Copyright (c) 2009 Tony Pitale

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
