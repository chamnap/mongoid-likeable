# mongoid-likeable
[![Build Status](https://secure.travis-ci.org/diowa/mongoid-likeable.png?branch=master)](https://travis-ci.org/diowa/mongoid-likeable)
[![Gem Version](https://badge.fury.io/rb/mongoid-likeable.png)](http://badge.fury.io/rb/mongoid-likeable)
[![Dependency Status](https://gemnasium.com/diowa/mongoid-likeable.png)](https://gemnasium.com/diowa/mongoid-likeable)
[![Code Climate](https://codeclimate.com/github/diowa/mongoid-likeable.png)](https://codeclimate.com/github/diowa/mongoid-likeable)
[![Coverage Status](https://coveralls.io/repos/diowa/mongoid-likeable/badge.png?branch=master)](https://coveralls.io/r/diowa/mongoid-likeable)

Add like to your Mongoid documents.
This is a fork of `tombell/mongoid-voteable` for people who only need likes.

**Note** Breaking changes from version 1.0 to 2.0. Check out our wiki for an update script

## Installation

Install the gem

    $ gem install mongoid-likeable

or add the gem to your `Gemfile`

    gem 'mongoid-likeable'

## Thread safety

This gem is thread safe.

## Usage

Include the `Mongoid::Likeable` module into your models you want to like.

```ruby
class Story
  include Mongoid::Document
  include Mongoid::Likeable

  # ...
end
```

You can then like by simply using the `like` method on the model.

```ruby
@story.like @user   # @user likes @story
@story.unlike @user # @user doesn't like @story anymore
```

You also have access to a helpful method.

```ruby
@story.liked? @user # true if @user likes @story
```
Like count is stored in a field called `likes`, so you can sort models by that field.

**Note** if your users are not stored in a Mongo collection or the ID field is
not called `_id` you can still pass the ID in as the second parameter instead.

```ruby
@story.like @user.id

@story.liked? @user.id
```

## License

mongoid-likeable is licensed under the BSD 2-Clause License

mongoid-voteable is licensed under the MIT License - Copyright (c) 2012 Tom Bell
