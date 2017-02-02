# TimezoneDropdown

Hi guys, this gem helps you to add a dropdown for timezone and change the timezone 
according to needs of user

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'timezone_dropdown'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install timezone_dropdown

## Usage

Include timezone.js in your appplication.js

    //= require timezone_dropdown

TODO: Add the below line where you want to add dropdown for time zone

```view
<select class="form-control" id="timezone"></select>
```

Add the below method in your controller with condition of your own for which you want the timezone to change.

```
around_action :set_time_zone

   private

   def set_time_zone
     Time.use_zone(current_user.timezone) { yield }
   end
```
For example you can use for a condition like this

```
 class ApplicationController < ActionController::Base
  around_action :set_time_zone

  def set_time_zone
    if logged_in?
      Time.use_zone(current_user.time_zone) { yield }
    else
      yield
    end
  end
 end 
```


For any other Timezone related queries vist <a href="http://api.rubyonrails.org/classes/Time.html">here</a>

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/timezone_dropdown. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Authored by: Shubham, shubham@rubyeffect.com

## About RubyEffect

![RubyEffect](http://blog.rubyeffect.com/wp-content/uploads/2015/05/cropped-re_original_logo.png)

RubyEffect builds intuitive, live and elegant software that solves real world problems. We love open source and it's community.

Liked this gem? You may also like the articles we post on our [blog](http://blog.rubyeffect.com). Please do check

We would love to work on your ideas and see them grow. Say hello @ http://rubyeffect.com/contact
